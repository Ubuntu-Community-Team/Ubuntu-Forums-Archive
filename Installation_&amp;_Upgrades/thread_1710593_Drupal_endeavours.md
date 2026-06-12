---
title: "Drupal endeavours"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by blackmail on 2011-03-20
Ok so i want to install drupal7 and i am pretty lazy and stupid regarding wep pages so here i go:

step 1
```
tasksel install lamp-setver
```

step 2
start the apache server

step 3
downloaded the drupal kit and unpacked the drupal folder in /var/www directory

step 4
type in the browser (FF 3.something) 127.0.0.1/var/www/drupal7/index.php

all well and nice till it said that it requires the config file
mainly here's the message:

```
Settings file	The settings file does not exist.
The Drupal installer requires that you create a settings file as part of the installation process. Copy the ./sites/default/default.settings.php file to ./sites/default/settings.php.
```

i am not sure what the config file is and what the sites/default directory is and where/how do i set it as default.

i am used to do stuff in php and to save my little scripts in the /var/www/something folder and run them from there the rest is rocket science for me! could someone help please

---

### Post by mariusse on 2011-03-21
> **blackmail said:**
> Ok so i want to install drupal7 and i am pretty lazy and stupid regarding wep pages so here i go:

step 1
```
tasksel install lamp-setver
```step 2
start the apache server

step 3
downloaded the drupal kit and unpacked the drupal folder in /var/www directory

step 4
type in the browser (FF 3.something) 127.0.0.1/var/www/drupal7/index.php

all well and nice till it said that it requires the config file
mainly here's the message:

```
Settings file    The settings file does not exist.
The Drupal installer requires that you create a settings file as part of the installation process. Copy the ./sites/default/default.settings.php file to ./sites/default/settings.php.
```i am not sure what the config file is and what the sites/default directory is and where/how do i set it as default.

i am used to do stuff in php and to save my little scripts in the /var/www/something folder and run them from there the rest is rocket science for me! could someone help please

Hello
You already get your answer from drupal > Copy the ./sites/default/default.settings.php file to ./sites/default/settings.php

You just have to rename the default.settings.php to settings.php then configure your database.
For a easy way to navigate thru your server i suggest you to install webmin for ubuntu [http://www.webmin.com/download.html](http://www.webmin.com/download.html)  

Regards

---

### Post by blackmail on 2011-03-22
Thank you this really helped a lot
I managed to install my drupal finally :D

Thanks again

---

### Post by tgalati4 on 2011-03-22
This step is documented in the README file in the Drupal directory, but if you don't find it, and don't create a starter settings file (settings.php), then the automatic installer fails.  I guess this is a security precaution to prevent automatic creation of Drupal sites.

---

