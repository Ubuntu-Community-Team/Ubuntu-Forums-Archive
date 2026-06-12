---
title: "nginx strange 404 Not Found errors"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by Giggitus on 2012-06-18
I have NGINX + Apache.

nginx.conf :

user nguser;
worker_processes  72;
timer_resolution  100ms;
worker_rlimit_nofile  8192;
worker_priority -20;

error_log  /var/log/nginx/error.log;
pid        /var/run/nginx.pid;

events {
    worker_connections  2048;
    use epoll;
    # multi_accept on;
}

http {
    include       /etc/nginx/mime.types;
    default_type application/octet-stream;

    #access_log    /var/log/nginx/access.log;
    access_log    off;
    
    log_format  main  '$remote_addr - $remote_user [$time_local] $status '
                      '"$request" $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "http_x_forwarded_for"';

    sendfile       on;
    tcp_nopush     on;
    tcp_nodelay    on;
    
    

    #keepalive_timeout  0;
    keepalive_timeout   65;

    gzip  on;
    gzip_disable "MSIE [1-6]\.(?!.*SV1)";
    gzip_min_length 1100;
    gzip_buffers 64 8k;
    gzip_comp_level 3;
    gzip_http_version 1.1;
    gzip_proxied any;
    gzip_types text/plain application/xml application/x-javascript text/css;

    include /etc/nginx/conf.d/*.conf;
    include /etc/nginx/sites-enabled/*;
}

----------------
In the conf.d folder next files 

apache.conf :

upstream apache {
    server   123.56.12.104:80;
}

--------------

proxy.conf

proxy_hide_header Server;
proxy_redirect off;
proxy_set_header  Referer  \$http_referer;
proxy_set_header  X-Real-IP  \$remote_addr;
proxy_set_header  X-Forwarded-For  \$proxy_add_x_forwarded_for;
proxy_set_header  Host \$http_host;
proxy_set_header  If-None-Match \$http_if_none_match;
client_max_body_size 500m;
client_body_buffer_size 16k;
proxy_connect_timeout 90;
proxy_send_timeout 90;
proxy_read_timeout 90;
proxy_buffer_size 16k;
proxy_buffers 16 128k;
proxy_busy_buffers_size 256k;
proxy_temp_file_write_size 256k;
proxy_headers_hash_max_size 51200;
proxy_headers_hash_bucket_size 6400;

-----------------

misc.conf :

server_name_in_redirect off;
server_tokens off;
#add_header X-Frame-Options SAMEORIGIN;
#keepalive_timeout 1200 1180;
keepalive_requests 10000;
server_names_hash_max_size 1024;
server_names_hash_bucket_size 128;

----------------

in the sites-enabled folder 

cam2camsite.com.conf :

###################################
### -- cam2camsite.com
###################################
server {
   listen 123.56.12.104:80;
   server_name  cam2camsite.com [www.cam2camsite.com]("http://www.cam2camsite.com") *.cam2camsite.com;
   
# Main location
   location / {
      gzip_static on;
      
      proxy_pass [http://123.56.12.104:8080/;](http://123.56.12.104:8080/;)
      proxy_redirect off;
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      
      proxy_connect_timeout 120;
      proxy_send_timeout    120;
      proxy_read_timeout    180;
      
      proxy_buffer_size          4k;
      proxy_buffers              4 32k;
      proxy_busy_buffers_size    64k;
      proxy_temp_file_write_size 64k;
           
      client_max_body_size       400m;
      client_body_buffer_size    128k;
    }
    
# Static files location
    location ~* ^.+.(jpeg|jpg|gif|png|bmp|ico|css|js|pdf|txt|doc|xls|xml|rtf|ppt|swf|exe|bar|apk|ipa|tar|tgz|gz|bz2|zip|rar|flv|avi|mp3|mpeg|mid|midi|wav)$ {
       root /home/www/sites/achat/cam2camsite.com/;
    }
    
    location ~ /.ht {
       deny  all;
    }
    
}

--------------

So, APACHE processed php files, NGINX processed static files.

But I have a strange problem with some pages.

[http://www.cam2camsite.com/online-dating/Micronesia](http://www.cam2camsite.com/online-dating/Micronesia) - opening without a problems

[http://www.cam2camsite.com/online-dating/Mexico](http://www.cam2camsite.com/online-dating/Mexico) - NGINX which dont have processed php say - 404 Not Found. But page are exist really.

[http://www.cam2camsite.com/online-dating/Mexico1](http://www.cam2camsite.com/online-dating/Mexico1) - really dont exist but opened

100% problem is not in my script, locally all pages work correctly. The problem is in NGINX setup.

Can somebody help me?

---

### Post by Giggitus on 2012-06-19
I found the problem!

[FONT=Arial][SIZE=2][COLOR=#000000][FONT=Arial][SIZE=2][COLOR=#000000]location ~* ^.+.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#000000]need to be[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#000000]location ~*  ^.+\.[/COLOR][/SIZE][/FONT]
otherwise nginx think that mexICO is ico file.

---

