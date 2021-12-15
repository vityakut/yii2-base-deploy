# Yii2 Base Deploy

Deploy Yii2 Base Application to Server via SSH by RSync

## Config example:

```
name: Build and Deploy
on:
    push:
        branches:
            -   master

jobs:
    build:
        name: Build and Deploy
        runs-on: ubuntu-latest
        steps:
            -   name: Checkout Repository
                uses: actions/checkout@master

            -   name: Setup Enviroment
                uses: shivammathur/setup-php@v2
                with:
                    php-version: '7.3'

            -   name: Install Packages
                run: composer install --no-dev

            -   name: Deploy to Server
                uses: yiier/yii2-base-deploy@master
                with:
                    user: user
                    host: host
                    path: path
                    owner: owner
                env:
                    DEPLOY_KEY: ${{ secrets.DEPLOY_KEY }}
```
