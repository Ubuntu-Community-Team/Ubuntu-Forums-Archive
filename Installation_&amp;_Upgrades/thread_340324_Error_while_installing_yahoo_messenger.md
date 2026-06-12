---
title: "Error while installing yahoo messenger"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by linax on 2007-01-17
Hi,

I downloaded yahoo messenger for debian from yahoo messsenger site. I logged in as root and then tried to install yahoo messenger as mentioned in the website but i keep getting this error.

dpkg -i ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 84219 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

What am i doing wrong? I installed xlibs using the synaptics. Well, at least i think so but not sure.

How do i fix this problem?

Rgds
Linax

---

### Post by ashmew2 on 2007-01-17
hi , if uve downloaded the debian package (yahoo_install.deb or something) from messenger.yahoo.com and ur using UBuntu then i think u shud be able to double click the deb file and select Install Package ? easy  ? :P

---

### Post by lukew on 2007-01-17
> **ashmew2 said:**
> hi , if uve downloaded the debian package (yahoo_install.deb or something) from messenger.yahoo.com and ur using UBuntu then i think u shud be able to double click the deb file and select Install Package ? easy  ? :P

Looks like it is a dependancy problem. It will be depending upon packages which are not in your repos. What repos do you have? Look at the installations instructions to find the dependancies.

On an off note I use  gaim which has yahoo messenger and msn etc all in one!! It also comes preinstalled.

Luke

---

### Post by ashmew2 on 2007-01-24
HI , whenever i try to use the .deb to install yahoo messenger it says "Dependency is not satisfiable : libssl0.9.6" Now im clueless what to do...Plz some1 help ,
 btw I am using gaim currently but it doesnt provide optimal support for transferring files , the windows clients dont recieve files i send even though if it has transferred 100% from my end..lol , Thanks

---

### Post by ashmew2 on 2007-01-26
HUrray!! got Yahoo messenger working at last!! :D I use dapper Drake and if u are having any dependency problems , read ahead!!
If you are having a dependency satisfiable error "xlibis" then download xlibs and install it by clicking here : [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb)

libgdk-Pixbuf2 dependency from here : [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fg%2Fgdk-pixbuf%2Flibgdk-pixbuf2_0.22.0-11_i386.deb&md5sum=2940d01c8ffa230c2a61d3f29dd3710b&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fg%2Fgdk-pixbuf%2Flibgdk-pixbuf2_0.22.0-11_i386.deb&md5sum=2940d01c8ffa230c2a61d3f29dd3710b&arch=i386&type=main)

Libssl0.9.6 from here :  Ive attached Libssl0.9.6 : [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fo%2Fopenssl096%2Flibssl0.9.6_0.9.6m-1_i386.deb&md5sum=01ca86d8c506bae38bacf93a2056efe9&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fo%2Fopenssl096%2Flibssl0.9.6_0.9.6m-1_i386.deb&md5sum=01ca86d8c506bae38bacf93a2056efe9&arch=i386&type=main)

and u need Yahoo Messenger (or what will u install LOL!!) : [www.messenger.yahoo.com](www.messenger.yahoo.com) 

and once Yahoo messenger is installed , u goto a terminal and type : ymessenger

Please let me know if this works on your computer!! It worked on mine!!

---

### Post by linbetwin on 2007-01-26
Here's my old howto for installing the lame Yahoo! Messenger client for Linux:

[http://ubuntuforums.org/showthread.php?t=81895](http://ubuntuforums.org/showthread.php?t=81895)

---

### Post by ashmew2 on 2007-01-26
Hey linbetwin , in ur howto it says "sudo aptitude install libssl0.9.6" but they are pretty old so they arent available from there...

---

### Post by Sef on 2007-01-26
Gyachi is a yahoo clone.  It has webcam and voice support, unlike Yahoo's im for Linux.

---

### Post by _hadi_ on 2007-05-08
Use this modified ymessenger package :)

---

