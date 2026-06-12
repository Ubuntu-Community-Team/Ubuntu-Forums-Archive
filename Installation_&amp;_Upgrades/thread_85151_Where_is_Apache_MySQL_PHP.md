---
title: "Where is Apache? MySQL? PHP?"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by firewood on 2005-11-01
I just installed Ubuntu 5.10 from the downloaded .iso, and everything went quite smoothly.  It installed nicely on my Compaq Presario 2500, which was a surprize, given my poor experience with other distros.

However, now I am stumped.  I want to set up a local Apache/MySQL/PHP development environment, but I see that none of the requisite packages are installed. I look in the "Add Applications" section, paging down through all the options, and find nothing about any of the applications I want.

When I do a "ps -ef | grep httpd" or likewise for mysql on the command line, there is nothing running for either of them.

Can someone point the way for me to get these very common, basic systems installed and running?

---

### Post by Kyral on 2005-11-01
sudo apt-get install apache2, mysql-server

Don't know how to get them running though

---

### Post by bacchus_3 on 2005-11-01
Have you tried to use Synaptic?  It's in System > System Administration (below Preferences) > Synaptic...

It should be included in the list...if not you may need to uncomment some lines in your /etc/apt/sources.list.

---

### Post by Stereotypical Rage on 2005-11-01
You need to enable the Universe and Multiverse repositories from your Sources.list file in /etc/apt

---

### Post by jdong on 2005-11-01
You need to:

(1) Enable the internet repositories -- these are not on the CDROM
(2) Enable Universe repository -- Some PHP packages reside there (don't worry -- Ubuntu still does nice security tracking for Universe PHP)

---

### Post by firewood on 2005-11-02
Found it all.  The answer was Synaptic.

---

### Post by MakubeX on 2005-11-04
is there a way that I can have both php4-mysql and php5-mysql installed in my system? if not, what version is recommended/usually used/preferred nowadays?

---

### Post by Chris Cromer on 2005-11-04
I don't know if you can have both installed. But I would think php5 would be more preferable, it's faster and has more features than php4. I am currently using php5 on this machine here.

---

### Post by yeahyeahyeah on 2005-11-28
What is the difference between Synaptic and the Ubuntu repositories.

Is it more like the Universal repository?


[QUOTE=firewood]Found it all.  The answer was Synaptic.[/QUOTE]

---

### Post by atoponce on 2005-11-28
[quote=yeahyeahyeah]What is the difference between Synaptic and the Ubuntu repositories.

Is it more like the Universal repository?[/quote]

The Ubuntu repositories are an online collection of software that is available to Ubuntu/Debian users.  Synaptic is a GUI Linux program to access the software that is in the repositories.  You will hear a lot about apt-get as well, which is a terminal program for accessing that software as well.

---

### Post by yeahyeahyeah on 2005-11-28
What's the difference between the "Add Applications" and Synaptic?

[QUOTE=atoponce]The Ubuntu repositories are an online collection of software that is available to Ubuntu/Debian users.  Synaptic is a GUI Linux program to access the software that is in the repositories.  You will hear a lot about apt-get as well, which is a terminal program for accessing that software as well.[/QUOTE]

---

### Post by jdong on 2005-11-28
Synaptic, because it shows all 15,000+ packages that are ready for you to install, may be too overwhelming for the newcomer...

The Add Applications tool (also known as gnome-app-install) is a simplified GUI that provides a very simplistic, user-friendly interface for installing a limited common subset of the Ubuntu package collection.

---

### Post by softgun on 2005-11-29
There is an Ubuntu server edition which has all these and more, including zope and postgresql in addition to what you want.
[http://ftp.ucr.ac.cr/ubuntu-cd/ubuntu-server/breezy/](http://ftp.ucr.ac.cr/ubuntu-cd/ubuntu-server/breezy/)

---

