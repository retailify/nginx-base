# Nginx-Base Docker Container

This images was build from the official NGINX source with compiled modules as described in the headline.

see: https://hub.docker.com/_/nginx

## Dockerhub image

[nginx-base](https://hub.docker.com/r/jproxx/nginx-base)

## Build

```bash
docker-compose up --build
```

## Enable Brotli compression

In your `nginx.conf` you have to load the compiled Brotli modules and switch Brotli on. You will find all configuration options in this github repository: https://github.com/google/ngx_brotli

```
load_module modules/ngx_http_brotli_filter_module.so;
load_module modules/ngx_http_brotli_static_module.so;

http {
   # other nginx configurations..... 

    gzip  on;
    brotli on;
    brotli_comp_level 6;
    brotli_static on;
    brotli_types application/atom+xml application/javascript application/json application/rss+xml
                 application/vnd.ms-fontobject application/x-font-opentype application/x-font-truetype
                 application/x-font-ttf application/x-javascript application/xhtml+xml application/xml
                 font/eot font/opentype font/otf font/truetype image/svg+xml image/vnd.microsoft.icon
                 image/x-icon image/x-win-bitmap text/css text/javascript text/plain text/xml;

   include /etc/nginx/conf.d/*.conf;
}
```
