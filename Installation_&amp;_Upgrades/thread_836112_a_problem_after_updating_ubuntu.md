---
title: "a problem after updating ubuntu"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by ramadan on 2008-06-21
after updating ubuntu the system cant load Xwindows (which i dont know), no screen found
i think the problem is with nvidia drivers( geforce8800 gt), so black screen and logon prompt is all i got after boot. how to fix this? and is there is any way to start the system in low graphics mode? every help is appreciated

---

### Post by Pumalite on 2008-06-21
Try this:
 Re: configure xserver
Xfix will re-create a basic, functional xorg.conf, but to really configure the Xserver you need to use displayconfig-gtk. Once you have the nvidia driver loaded from the Hardware Drivers menu, press alt-F2 to get a command line, then enter
Code:
gksudo displayconfig-gtk

---

### Post by ramadan on 2008-06-21
:confused:, Once you have the nvidia driver loaded from the Hardware Drivers menu?
do you mean during booting? would you please simplify it

---

### Post by Pumalite on 2008-06-21
Did you have an Nvidia driver installed before the kernel upgrade?

---

### Post by ramadan on 2008-06-21
yes, using envy, then ..there is new upadates click this ballon.. and i did, after restarting the system cant load the graphical interface, so how to deal with it, i didnt want to reinstall ubuntu again, another point is ubuntu is the most easy to use linux? also is there place to find line commands of ubuntu explained

i tried the command you suggest me>> gtk-warnning**: cant open display

---

### Post by Pumalite on 2008-06-21
This might help:
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by ramadan on 2008-06-21
thanks, I'll try to do some homework :)

---

### Post by Pumalite on 2008-06-21
You are welcome. Good luck.

---

