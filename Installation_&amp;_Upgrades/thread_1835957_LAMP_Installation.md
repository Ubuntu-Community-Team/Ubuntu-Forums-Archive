---
title: "LAMP Installation"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by vikrantalmelkar on 2011-08-30
Hi Team,

I am trying to install Mediawiki, but it requires me to install LAMP.

can you please guide me in installing LAMP on Ubuntu 11.04

Appreciate the help very much

thanks
Vik

---

### Post by iponeverything on 2011-08-30
l = linux 
a = apache
m = mysql
p = php


I assume the l is good.

use the package manger to install a, m and p.

---

### Post by mhart on 2011-08-30
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

mysql, apache, ftp

---

### Post by mörgæs on 2011-08-30
In Ubuntu you should almost never download stuff from the web and install it. This is a bad habit from Windows. In stead:


```
sudo apt-get install tasksel

sudo tasksel install lamp-server
```

In short, more or less everything of value is in the repositories.

---

### Post by vikrantalmelkar on 2011-08-31
Hi Mourgaes,
 
Danke Sehr for your help. with those Command line the jod was easy.
 
now I need to figure out how to configur mediawiki with the skins and the content
 
any help is appreciated
 
Thanks very much
Vik

---

### Post by mörgæs on 2011-08-31
You are welcome.

I don't know Mediawiki. Have you tried this?
[http://www.mediawiki.org/wiki/Installation](http://www.mediawiki.org/wiki/Installation)

---

