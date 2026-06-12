---
title: "[solved] Ubuntu 14.04 - PHP7 version - problem of install with ondrej ppa"
date: 2019-05-08
forum: Installation &amp; Upgrades
---

### Post by smalldragoon on 2019-05-08
Hi, 
I need to have a PHP7.x on an Ubuntu 14.04.
I followed some tutorials with the ondrej ppa but it never grab any php version except the PHP5.x versions.
I tried the tricks with locales , clear all PPA... nothing
IS there a way to install php7 on a 14.04 ? 
Thanks !

---

### Post by dino99 on 2019-05-08
Have you followed that howto ? [https://www.digitalocean.com/community/tutorials/how-to-upgrade-to-php-7-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-upgrade-to-php-7-on-ubuntu-14-04)

---

### Post by smalldragoon on 2019-05-08
Hi, Thanks for your interest.
Yes I did. With and without the locales trick

---

### Post by Holger_Gehrke on 2019-05-08
if [that is the PPA]("https://launchpad.net/~ondrej/+archive/ubuntu/php/+index") you're trying to install from then I've got bad news for you: "Only Supported Versions of PHP ([http://php.net/supported-versions.php](http://php.net/supported-versions.php)) for Supported Ubuntu Releases ([https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)) are provided". Support for 14.04 is over AFAIK (or will be very shortly) and the PPA has no packages for that release anymore.

Holger

---

### Post by smalldragoon on 2019-05-09
Hi Holker, 
I foudn this before, but read it wrongly yhrn, thanks :(
is there a way to install 7.X on a Ubuntun 14.04 then ? ( I don't need special features such as co exisint 5.5 and 7.X ..) just a 7.X ... whatever it is ...
thx

---

### Post by TheFu on 2019-05-09
If you have an extended support contract with Canonical, contact them.  For the rest of us, support for 14.04 ended last month. Move to 16.04 or 18.04, those are the only choices.

---

### Post by smalldragoon on 2019-05-10
that was my fear... 
Thanks a lot to all

---

### Post by Topsiho on 2019-05-12
I have found this website:

[https://websiteforstudents.com/php-7-3-released-heres-how-to-install-upgrade-on-ubuntu-16-04-18-04-18-10/](https://websiteforstudents.com/php-7-3-released-heres-how-to-install-upgrade-on-ubuntu-16-04-18-04-18-10/)

and I suggest that you install 16.04, or better still, 18.04, and follow the instructions on this website.

Installing a new Ubuntu is very easy, and doesn't take much time if you have good internet connection.
Back up first all data (documents, etc, in your home ditectory, which you don't want t loose).

Why was this thread marked as solved, while it wasn't ?

Topsiho

---

### Post by smalldragoon on 2019-05-12
Hi, Issue is solved as you can not install PHP7 anymore on 14.04. Support has ended.( see port from Holger )
I reinstalled a 18.04 which allowed me to do what I needed

---

