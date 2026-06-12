---
title: "Upgrade tp feisty: terminal broke"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by mannantai on 2007-05-12
Hi i'm a newbie using Xubuntu. 
I just upgraded from 6.10 to 7.04. All went almost ok, but just before starting the cleaning process it said something like "Fatal error configuring X" and the upgrade process stopped. 
Now everything seems to be working, but when i try to start the terminal my session stops and i found myself logged out.  :( 
Any idea on why? and is there some way to have the terminal back? :confused: 

I checked Syslog and found this: 
 gdm[4385]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
The file messages seems all right. 

Thanks for any help you'll give
edit: Hope this is the right section of the forum. I updated using the update manager, after updating all my programs.

---

### Post by john_spiral on 2007-05-12
looks like a Xorg crash error.

backup all your files and try a clean install. Anyone else?

---

### Post by BertjeBebo on 2007-05-12
me

u can work around with xterm

cf. [http://ubuntuforums.org/showthread.php?t=434523&highlight=xubuntu+terminal](http://ubuntuforums.org/showthread.php?t=434523&highlight=xubuntu+terminal)

howto file a bug?

---

### Post by mannantai on 2007-05-15
Hi, i saw there's a bug already reported on this and i found the solution to the problem in the bug report thread. 
[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849)
You just need to find xorg.conf in etc/x11 and change colour depth from 24 to 16. That does the trick. :guitar: 
I have no idea why, though. :lolflag: 
Does anybody know exactly what colour depth is all about?

---

