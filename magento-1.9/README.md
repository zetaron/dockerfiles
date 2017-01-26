# Magento 1.9.x docker development environment
## Requirements
- [direnv](https://github.com/direnv/direnv)
- [dns-gen](https://github.com/zetaron/docker-dns-gen)
- [docker-compose](https://docs.docker.com/compose/install/)
- [mkpem](https://gist.github.com/zetaron/4ec728939dc0db1f08bccd55140b5746)

## Optional Requirements
- [mycli](http://mycli.net/)
- [python2](https://www.python.org/download/releases/2.7.8/)
- [python2-yaml](http://pyyaml.org/)
- [jq](https://stedolan.github.io/jq/)

## Installation
Copy the `.envrc` and `docker-compose.yml` files into your projects root directory.
Edit the `.envrc` file, and modify the following variables:
- `COMPOSE_PROJECT_NAME`
- `DNS_GEN_TLD`

## Usage
### First startup
1. Place one `.sql`, `.sql.gz` or `.sh` file inside your `<PROJECT_DIR>/var/sql` directory to initialize your database.
2. direnv allow <PROJECT_DIR>
3. Run the `up` command.

### View logs
To view all logs simply run the `logs` command.
If you need to view the logs of a specific service it is nearly as simple as to view all logs, you just need to append the services name.
Like this `logs <my_service_name>` eg. `logs magento` or `logs mysql`.

### Tear down the projects servers
Run `down`

### Import a new database
Place the dump file into your `<PROJECT_DIR>/var/sql` directory and run the following commands.

```shell
cd <PROJECT_DIR>
down
docker volume rm <PROJECT_NAME>_db
up
```
