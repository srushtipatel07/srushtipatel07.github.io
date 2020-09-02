
# Basic Routing in React JS

Routing is a basic thing you need in your website . Routing is used for navigating one page to another .
So We are going to learn how to navigate one page to another in ReactJS.
Let's Start !
 
  **ReactJS Installation**
		You’ll need to have Node >= 8.10 and npm >= 5.6 on your machine.
 1. So first install NodeJS . 
 2. Check NodeJS version by command

```
node -v
```  
3. Check npm version by command
```
npm -v
```
This will create basic project srructure for your application.
*  **Installing dependencies**
  
Go to your project directory
```
cd basic-routing
```
Execute below command to install dependecy for react routing.
```
npm install --save react-router-dom
```
check your package.json file in project directory . Dependency will be updated in dependencies list.

React router API provides two types of router.
1. ``` <BrowserRouter> ```
2. ``` <HashRouter> ```
   
 ``` <BrowserRouter> ``` is used for dynamic routes and most popular router among the two.

 ``` <HashRouter> ```  is used for static routing it consist hash  (#) in every URL .

 ```
 // <BrowserRouter> URL

 http://routerexample.com/basic

 // <HashRouter> URL

  http://routerexample.com/#/basic

  ```

  Here , WE are creating Three pages for Routing .So first WE create components for them.

  Below are the Code Snippets for Pages components.

  **Home Page**

   > **src/components/pages/Home.js**
   ```
import React , { Component } from 'react';

class Home extends Component {
    // eslint-disable-next-line no-useless-constructor
    constructor(props){
        super(props);
    }

    render(){
        return (
            <div>
                <h2> Home  </h2>
                <p> Home page Body Content </p>
            </div>
        );
    }
}

export default Home;
```
 **About Page**

   > **src/components/pages/About.js**
   ```
   import React from 'react';
import { Component } from 'react';

class About extends Component {
     // eslint-disable-next-line no-useless-constructor
     constructor(props){
        super(props);
    }

    render(){
        return (
        <div>
            <h2> About Us  </h2>
            <p> About Us page Body Content </p>
        </div>
        );
    }
}

export default About;
```
**Contact Page**

   > **src/components/pages/ContactUs.js**
   ```
import React , { Component } from 'react';

class ContactUs extends Component {
      // eslint-disable-next-line no-useless-constructor
      constructor(props){
        super(props);
    }

    render(){
        return (
            <div>
            <h2> Contact Us  </h2>
            <p> Contact Us page Body Content </p>
        </div>
        );
    }
}

export default ContactUs;
```
Here We also create PageNotFound component for any mismatching URLS. 

**Page Not Found Page**

   > **src/components/pages/PageNotFound.js**
   ```
   import React , { Component } from 'react';

class PageNotFound extends Component {
    // eslint-disable-next-line no-useless-constructor
    constructor(props){
        super(props);
    }

    render(){
        return(
        <div>
            <h2> 404 - Page Not Found   </h2>
            <p>  Ooops ! Page Not Found  </p>
        </div>
        );
    }
}

export default PageNotFound ;
```
Now We make navigation bar .

**Navigation Bar component**

   > **src/components/common/Navbar.js**
   ```
/* eslint-disable no-useless-constructor */
import React from 'react';
import { NavLink, Link } from 'react-router-dom';

class Navbar extends React.Component {

        constructor(props){
            super(props);
        }

        render() {
            return (
                    <nav className="navbar navbar-expand-sm bg-dark navbar-dark">
                            <ul className="navbar-nav nav-pills">
                                <li className="nav-item">
                                    <NavLink className="nav-link"  to='/home' > Home</NavLink >
                                </li>
                                <li className="nav-item">
                                    <NavLink className="nav-link" to='/about'> About US</NavLink>
                                </li>
                                <li className="nav-item">
                                    <NavLink className="nav-link"  to='/contact'> Contact Us</NavLink>
                                </li>
                            </ul>
                    </nav>
            );
        }

}

export default Navbar;
```
Navigation Bar component uses ```<NavLink>``` component which is provide by router. 

```<Link>``` and  ```<NavLink>``` components both are used to navigate the different routes on site , but  ```<NavLink>``` have an extra functionality to add the styles to the active routes.

Now We finally define routes for site.

**App component**

   > **src/App.js**
   ```
   import React from 'react';
import './App.css';
import { BrowserRouter, Route, Switch } from 'react-router-dom';
import Navbar from './components/common/Navbar';
import Home from './components/pages/Home';
import About from './components/pages/About';
import ContactUs from './components/pages/ContactUs';
import PageNotFound from './components/pages/PageNotFound';

function App() {
  return (
    <div className="App">
      <h2> Basic Routing By React</h2>
      <BrowserRouter>
          <Navbar/>
          <div className="container-fluid  p-3 my-3 bg-dark text-white" >
          <Switch>
            <Route exact path="/" component={Home}/>
            <Route exact path="/home" component={Home}/>
            <Route exact path="/about" component={About}/>
            <Route exact path="/contact" component={ContactUs}/>
            <Route component={PageNotFound}/>
          </Switch>
          </div>
      </BrowserRouter>
    </div>
  );
}

export default App;
```
Here We use ```<BrowserRouter>``` . Add ```<Navbar>``` for navigation menu.

```<Switch>``` and ```<route>``` are used to define  route components.  ```exact```  keyword in ```<Route>``` matches the exact path with URLs. if we avoid to use ```exact``` then it will match both ```/``` and ```/home``` and  as well as others.

Here , We define component in routes based on pages with **component**  property. ```PageNotFound```  component is defined in last route. So whenever any URL will not match with defined routes it will render ```PageNotFound```  component.

For better view , add some styles.

add below links to index.html in your project.

```
// add this to <head> tag 
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" />

// add below scripts to <body> tag 

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js"></script>

```

Now Run the application with below command
``` 
npm start 
 ```

After server start sucessfully , It will Launch application on 
http://localhost:3000 by default.
