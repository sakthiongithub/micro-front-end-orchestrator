# Micro frontends Orchestrator


This is a simple application that demonstrates one approach to creating 
[Micro frontends]
using [Web Components](https://developer.mozilla.org/en-US/docs/Web/Web_Components) to integrate different web apps. 


There are several sub-projects in this repo:

* `orchestrator` - Entry point for the app; simple HTML page that uses the [Vaadin Router](https://vaadin.com/router) 
web component to dynamically 
load different micro frontends.
* `app-one` - Simple web app that uses Web Components. Built with `lit-element` and `lit-html`, and uses the  web component.
* `app-two` - Default app created using the [Angular](http://angular.io) 8 CLI, but packaged as a web component via 
[Angular Elements](https://angular.io/guide/elements).
* `app-three` - Another Angular 8 created via the CLI and packaged via Angular Elements, but this one uses the [PrimeNG 
Table] component to talk to the `app-three-service` microservice.
* `app-three-service` - Simple microservice built using Java and the [MicroProfile](https://microprofile.io/) standard 
running on [Payara Micro](https://www.payara.fish/software/payara-server/payara-micro/); returns canned data.

> NOTE: This project does not currently use any polyfills for Web Components or other standards, so evergreen browsers 
are required. (If you want polyfills, you'll need to add them from https://github.com/webcomponents/polyfills)

It's theoretically possible to include other technologies using this method, such as React via Adobe's 

## Running 

First, make sure you have Node (for JS/TS) and Maven (for Java) installed.

1. Download dependencies and build each app as described in the individual README located in the app's folder.
2. Run `app-three-service` as described in the project's README.
3. Run a web server from the root folder, and point it to `orchestrator/index.html`. For simplicity, the project
includes express, which can be used to serve the app.

To setup express, install the dependencies:
    
```
 npm install 
```

Then run the server:

```
cd <root folder of this repo>
node server.js
```
And point your browser to the URL indicated (usually `http://127.0.0.1:8000`).

> Technically, all of these apps could run on separate servers (using  
[CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) headers) or be proxied through the main web server.

