<p align="center"><img src="https://enmemolab.com/app/github/starter.png"></p>

# Laravel Vue SPA

A copy of the best framework of all "Laravel 6 and Vue Cli".
This copy is the ini point with Vue Cli and laravel integration.

## What is installed!

> Laravel 6
> Vue 2.6.10
> Vuex 3.1.1
> Vue Router 3.1.3

### Start the installation Laravel and NPM packages

-   Clone this repository
-   Rename `.env.example` to `.env`
-   `composer install`

Or if you need to start from cero

    ``` sh
    laravel new my-project
    cd my-project

    # remove existing frontend scaffold
    rm -rf package.json webpack.mix.js yarn.lock resources/assets resources/js resources/sass
    ```

### Files that I modified  

- `I created a new controller for the main view (Frontend)`
- `I add the route in /route/web.php`
- `I rename the welcome.blade.php to main.blade.php in /resources/views`

### Create a Vue CLI project inside Laravel

- `When creating the project you must call it (frontend)`

    ```
    vue ui (or) vue create frontend
    ```

### Configure Vue project

    Create `frontend/vue.config.js`:

    ``` js
    module.exports = {
      // proxy API requests to Valet during development
      devServer: {
        proxy: 'http://laracon.test'
      },

      // output built static files to Laravel's public dir.
      // note the "build" script in package.json needs to be modified as well.
      outputDir: '../public',

      // modify the location of the generated HTML file.
      // make sure to do this only in production.
      indexPath: process.env.NODE_ENV === 'production'
        ? '../resources/views/main.blade.php'
        : 'index.html'
    }
    ```

    Edit `frontend/package.json`:

    ``` diff
    "scripts": {
      "serve": "vue-cli-service serve",
    - "build": "vue-cli-service build",
    + "build": "rm -rf ../public/{js,css,img} && vue-cli-service build --no-clean",
      "lint": "vue-cli-service lint"
    },
    ```
### To Run the Frontend

``` sh
cd frontend
yarn # OR npm install
yarn serve # OR npm run serve

# build for production:
yarn build # OR npm run build
```
