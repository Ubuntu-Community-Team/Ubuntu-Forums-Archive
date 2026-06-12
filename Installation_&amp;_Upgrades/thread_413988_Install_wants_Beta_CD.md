---
title: "Install wants Beta CD"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by PtheS on 2007-04-19
I'm trying to add LAMP and FTP to 7.04. I had installed the beta and now how full release. When I try to install LAMP using

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

I get the following message:

Media change: please insert the disc labeled
 'Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)'
in the drive '/cdrom/' and press enter

Regardless of which CD I stick in the drive the message stays.

What can I do?

---

### Post by bwhite82 on 2007-04-19
Edit your sources.list and get rid of any lines that have "deb cdrom...":

> sudo gedit /etc/apt/sources.list


Then proceed to install what you are trying to install. APT still thinks you have the beta CD available to pull packages from. Alternately, if you want to use the new CD (if you have one), insert the disc and type the following:
> 
sudo apt-cdrom add

---

