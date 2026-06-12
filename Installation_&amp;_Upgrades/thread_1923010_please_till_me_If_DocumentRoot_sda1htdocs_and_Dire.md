---
title: "please till me If DocumentRoot /sda1/htdocs and Directory /sda1/htdocs is good ?"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by laith1952 on 2012-02-09
hi,
please till me If
DocumentRoot /sda1/htdocs and 
Directory /sda1/htdocs
is good in ubuntu 10.10 ?
with many thanks
 
<VirtualHost *:80>
ServerAdmin webmaster@localhost
 
DocumentRoot /sda1/htdocs
 
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
 
<Directory /sda1/htdocs>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory

---

