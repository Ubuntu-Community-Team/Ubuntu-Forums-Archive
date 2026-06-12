---
title: "Control of boot default"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-02-02
**First**, I am now trying to configure and setup my Ubuntu 9.10 desktop. However, I still need to use Windows Vista. I would like to change the bootup default to Windows Vista instead of Unbuntu. That is.
 
Ubuntu,...
Ubuntu,...
Memory Test ...
Menory Test ...
Windows Vista (loader)(on/dev/sda1)
 
I would like for the default to be the last entry, not the first. How can I change this?
 
Second, I was able to connect to the Web with Firefox with no problem. However, there a character encoding problem that I have been unable to solve.
 
My homepage is:
 
[http://www.it.uu.se/edu/course/homepage/simopsyst/p2ht09/](http://www.it.uu.se/edu/course/homepage/simopsyst/p2ht09/)
 
and if one looks at the source, this has charset=utf-16. However, I have been able to get Firefox to recognize this. Any ideas on how I can get Firefox to detect and use the correct character encoding?
 
--V

---

### Post by jerrrys on 2010-02-02
i use **startupmanager** for this.  its in synaptic package manager

---

### Post by efflandt on 2010-02-02
The easiest way to default to whatever you booted last (assuming grub2) is to change **GRUB_DEFAULT=0** to **saved** like this in this part of /etc/default/grub (you can do that with **sudo nano** or **gksu gedit**).  The leading # comments out that line so it is ignored, but so you still know what it was if you want to change it back:

#GRUB_DEFAULT=0
GRUB_DEFAULT=saved

Then do **sudo update-grub**.

Then if you booted Windows last, it would default to Windows, and if you booted Ubuntu last it would default to that.

---

