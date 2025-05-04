# simple_wordpress_compose

This compose file exists to make it easy to do Wordpress theme development locally. 

## Usage

To use this setup:
1. [**One Time Only**] Create the permanent volumes (see [Volumes](#volumes) section below)
2. Run `docker compose up -d` in this directory
3. Access your Wordpress site at [http://localhost:8080](http://localhost:8080)

Your theme should be accessible from the Wordpress admin page, though it will be broken until you add appropriate files to your custom directory. 

When finished: 

3. Run `docker compose down` in this directory


## Volumes

Two volumes must exist before running this compose file. I recommend configuring the first one to bind to a local directory. This will make theme development easier. 

The second is to ensure that your database is not tied to a container's lifetime. It's probably easier to not bind this one to a local directory, but it's up to you. 

```
 docker volume create \
    --driver local \
    --opt type=none \
    --opt device=PATH_TO_WORDPRESS_THEME_DIRECTORY \
    --opt o=bind \
    simple_wordpress_wp_custom_theme
 ```

```
docker volume create simple_wordpress_wp_database
```
