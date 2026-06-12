---
title: "Apache 2 installation"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by zapper on 2007-01-27
Hi,

I have installed apache 2 and php 5 on my ubuntu machine. I have also installed libapache2-mpd-php5. However php is still not working on my machine with apache. When I try to view a php file it asks me for downloading.. Do I need to change a config file somewhere? Right now, all comfig files are in there default state.

Just added php5.conf and php5.load from  mods-available to mods-enabled.. However It is still not working..:(

---

### Post by Koybe on 2007-01-28
> **zapper said:**
>  Just added php5.conf and php5.load from  mods-available to mods-enabled.. However It is still not working..:(


To do this, you only need :
```
sudo a2enmod php5
sudo /etc/init.d/apache2 force-reload
```

---

