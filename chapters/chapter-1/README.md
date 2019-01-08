# Chapter 1

# Set up dev environment

Prerequisites
  - Install visual studio code
  - Install node

# Init node & typescript

Open a terminal window in your project directory.

To create your package enter `npm init`. Follow instructions on screen to create your *package.json* file.

---
A package.json file:
* lists the packages your project depends on
* specifies versions of a package that your project can use using semantic versioning rules
* makes your build reproducible, and therefore easier to share with other developers

Source: [npm docs](https://docs.npmjs.com/creating-a-package-json-file)

---
Init **Typescript** in your project with `tsc --init`

# Project folder structure

public
--index.html
src
--app.ts
package.json
tsconfig.json

Start with creating **src/app.ts** and add some dummy code to it.

```
const hello = () => alert("Hello typescript!");
hello();
```

The file **app.ts** will be the main entry of your web application.

Update tsconfig.json to save all the compiled code in **public/app.js**

"outFile": "./public/app.js"

Also set the module code generation to 'none' (No questions asked here);

"module": "none"

# Build your first typescript code
You can compile your typescript code using the command `tsc`. 

However, to make it more generic we are going to add a build script to your project.

Do this by updating the scripts of **package.json**

```
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "tsc"
}
```

You can remove the **test** script if you would feel the need for it.

Now build your project with `npm run build`

---

**Visual studio code tip:** configue a default build task as follow:
* *Terminal -> Configure default build task...*
* Select: *npm: build*
* From now on, you can press **ctrl+shift+b** to build build your project

---

The **public** folder should now contain a **app.js** file containing the compiled typescript code.

# Load the code in your app
Our web application should know to load the **app.js** file.

Create an **index.html** file in the **public** folder and add the javascript file to it.

# Create a local development server
Several solution exist for this but I have found **lite-server** quite easy to use.

Install **lite-server** as a dev dependency to your package.

```
npm install lite-server --save-dev
```

---
**--save-dev** is used to save the package for development purpose. Example: unit tests, minification..
**--save** is used to save the package required for the application to run.
---

Add a new script in **package.json** to start up your development server.

```
    "server": "lite-server --baseDir ./public"
```

Now you can start your server with `npm run server`. A browser window will open with **http://localhost:3000**. An alert box should display: "Hello typescript!"
