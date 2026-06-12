---
title: "Install software on external drive"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by ultimalrage on 2011-08-26
Hi,

Is there any way to use apt-get to install software on /media/usb or some place like that, instead of the root fs?

Thanks.

---

### Post by ottosykora on 2011-08-26
dont know if apt-get can be forced to do it, but even if it can, then it depends very much on the software you have in mind. 
If the software is some single executable and all libs it depends on are installed locally, well all might work. 
On my 32bit ubuntu, I have some sotware which is not from the repositories here and this is simply delivered as a folder with few things it it and will work this way.

However the software packages here will install also all the libs to some place like /usr/lib/.... and other things to other places, so it is not so simple to have basicaly 'portable' apps for ubuntu.

But they do exist.
[http://portablelinuxapps.org/](http://portablelinuxapps.org/)

there you will find most important programs like browsers, mail clients and similar which can be 'installed' to separate drive and might work on many mainstream linux distros.

---

### Post by ultimalrage on 2011-08-26
I need MySQL, Asterisk, Apache, Perl and PHP installed on the external drive. I am working with the ARM port of ubuntu. I would have built it all from scratch but cross-compiling all this is a pain. The repository has the packages, only issue is system flash on the device doesn't have space to store all this. I need to store all this on the external drive. Only other alternative would be to actually boot ubuntu off the external drive and then install stuff from the repo.

---

