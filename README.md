# accdk website

## Digital Ocean Ubuntu VPS setup

IP: 138.68.81.163

```
sudo mkdir -p /var/www/accdk.org/html
sudo chown -R $USER:$USER /var/www/accdk.org/html
sudo chmod -R 755 /var/www/accdk.org
vim /var/www/accdk.org/html/index.html
sudo vim /etc/nginx/sites-available/accdk.org
sudo ln -s /etc/nginx/sites-available/accdk.org /etc/nginx/sites-enabled/
```
```
sudo vim /etc/nginx/nginx.conf
sudo nginx -t
```

Find the server_names_hash_bucket_size directive and remove the # symbol to uncomment the line


In file `sudo vim /etc/nginx/sites-enabled/default`
change root to `root /var/www/accdk.org/html;`

Read  `./How To Install Nginx on Ubuntu 18.04 | DigitalOcean.pdf`

## Install

Install ruby

### Compile scss

Install ruby sass

`gem install sass`

To compile manually use

`sass assets/sass/main.scss assets/css/main.css`

or run command below in the background during development

`sass --watch assets/sass/main.scss:assets/css/main.css`

## Deploy

`rsync -avz --exclude 'conf' --exclude '.git' --exclude '.sass-cache' . root@138.68.81.163:/var/www/accdk.org/html`
