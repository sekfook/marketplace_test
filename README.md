# marketplace_test
# xai-marketplace

The Xpress AI Marketplace system that gives data scientists using Engine
access to datasets, pre-trained models, components and templates.


## Dev environment.

This repository uses docker for development.  The docker-compose.yml file
contains services for the db (mysql), wordpress with woocommerce and the 
app.

If you are running for the first time or have changed the 
marketplace/Dockerfile file you must first build the container for the app
with the following command:

```sh

docker-compose build

```

Then to start the mysql and apache container run:

```sh

docker-compose up
```

Install the vendor libraries by running the following commands:

```sh
docker exec -it xai-marketplace_marketplace_1 bash
php composer.phar install
```

You can then access the application at http://localhost:8000/

The files are mounted into the container and changes will be applied immediately.

Wordpress can be accessed at http://localhost:8080/.  Open it in a browser 
and create an admin account and install the woocommerce plugin.


## Cleaning up

Press Ctrl-C to stop the containers.  The data will remain in the db_data
folder.

To remove the containers from disk completely and clear the DB run:

```sh

docker-compose down
docker-compose rm
rm -r db_data/*
```


## Testing

To run the unit tests open a new terminal and run:

```sh

docker exec -it xai-marketplace_marketplace_1 bash
./vendor/bin/phpunit
```

If all the tests run successfully you'll see:

```
..                                                                  2 / 2 (100%)

Time: 00:00.419, Memory: 10.00 MB

OK (2 tests, 2 assertions)
```

testing
