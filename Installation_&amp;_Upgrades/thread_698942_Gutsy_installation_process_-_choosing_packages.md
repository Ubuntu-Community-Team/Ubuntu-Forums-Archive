---
title: "Gutsy installation process - choosing packages"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2008-02-16
When I installed Feisty it took a couple of false starts to get the packages I wanted.  I ended up installing from the full DVD and being able to select desktop features plus LAMP server applications.  I'm trying to do the same kind of thing now - installing Gutsy on a laptop, but needing server capabilities and also source so that I can play with the wireless drivers.  

But I can't figure out how to do this as easily with Gutsy.  The Synaptic Package Manager has lots of packages, but how do I figure out which combination to install?  For example, what's the difference between apache2 and apache2.2-common?  And why are some of the packages in Base System not installed.

Thanks

---

### Post by dabang on 2008-02-17
Installing any Ubuntu version from the default desktop CDs leaves you with a well configured desktop system - and that's the way it's supposed to be. If you need server-only apps you could try the server install CD (I have no experience with that). If I get you right, you'd like to have a desktop system with some server apps installed? That's quite easy and I don't really know where the problem is? If you need an apache webserver go to synaptic and install apache2 it'll pull all dependencies (like apache2-common) onto your box. If you need any header files go and install the appropriate "dev" packages. For a LAMP server I'd install the following:
```
sudo apt-get install apache2 libapache2-mod-php5 php5-mysql php5 mysql-server
```
That would be the basic installation. You could add
[LIST]
[*]phpmyadmin
[*]mysql-admin
[*]mysql-navigator
[*]mysql-query-browser
[/LIST]
Hope I could help!

---

