---
title: "php 7.1 on Ubuntu 18.04"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by howardsmiller on 2018-04-30
I have just upgraded to 18.04 and see it comes with PHP 7.2.   I really need to run php 7.1. I can't get it to work. 

I did something like)

$ a2dismod php7.2
$ apt install php7.1
$ a2enmod php7.1

...which all worked, but I can no longer start apache

To cut a long story short /usr/lib/apache2/modules/libphp7.1.so is missing. (the module loader references it)

I can't figure out how to get this file (or what else I might have done wrong). 

Any pointers appreciated

---

