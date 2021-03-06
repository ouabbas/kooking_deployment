
# Newbrands deployment

Repo qui contient les directives docker pour le serveur proxy nginx et la production de certificats

## Installation

Install git in AWS EC2

```bash
  sudo yum install -y git
```
    
Install docker in AWS EC2

```bash
  sudo amazon-linux-extras install docker
  sudo service docker start
  sudo usermod -a -G docker ec2-user

  # Make docker auto-start:
  sudo chkconfig docker on

  # Reboot to verify it all loads fine on its own:
  sudo reboot

  # Check if docker is installed:
  docker -v
```
    
Install docker-compose in AWS EC2

```bash
  sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
  sudo chmod +x /usr/local/bin/docker-compose

  # Check if docker-compose is installed:
  docker-compose -v
```

## Some commands

Test certificate

```bash
  docker-compose run --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ --dry-run -d api.kooking.app
```

Create certificate (just remove the flag --dry-run)

```bash
  docker-compose run --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ -d api.kooking.app
```

## Authors

- [@ouabbas](https://www.github.com/ouabbas)
