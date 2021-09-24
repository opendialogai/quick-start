# OpenDialog Prebuilt Docker Image

The OpenDialog CI process builds a Docker image for releases and main feature branches. This docker-compose configuration helps you to quickly get started with the latest build of OpenDialog from the Opendialog Docker hub [registry](https://hub.docker.com/repository/docker/opendialogai/opendialog).

## Running Docker locally

To run OpenDialog from a Docker image, you should use the `docker-compose.yml` file included with this project.

The `docker-compose` file defaults to the tag `1.x` which should have the latest OpenDialog docker image.

You can change line 4 of the `docker-compose.yml` to set a different tag from the OpenDialog public DockerHub [repository](https://hub.docker.com/repository/registry-1.docker.io/opendialogai/opendialog/tags).

Get the application up and running use: 

    `docker-compose up -d app`

After first run, or to update a running application, the `docker-update.sh` script needs to be run. To run this within in the app container, run the following:

    `docker-compose exec app bash docker/scripts/update-docker.sh`
    
This will run all database migration files, set up the webchat settings, optionally load all conversations and create the default admin user (if not already created).

You can then visit `http://localhost` and you should be able to login to the OpenDialog application (user:admin@example.com \ password: opendialog)

If you need a newer copy of the same image, power down the app with
 
 `docker-compose down`

pull the new image

`docker pull opendialogai/opendialog:1.x`

replacing dev with the tag you are interested in and then start it up again. 

` docker-compose up -d --force-recreate app`

    
