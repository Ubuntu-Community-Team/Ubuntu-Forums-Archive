---
title: "back to ubuntu, now this...."
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by killer62491 on 2012-02-18
Been a while since I have attempted an Ubuntu install, and now when I did the install using Wubi, it says some error I cant remember, but I'll see if I can find the error log in a minute. I will be active in the meantime, so feel free to pm me once i return with the error message posting. Also, is it possible to somehow mount an ISO file of the disc image for Ubuntu installations? If so, can it be used to install Ubuntu? Any feedback is appreciated!

.:ALPHA::HECTOR::SIERRA:.

---

### Post by darkod on 2012-02-18
On vista and 7 in most cases you need to run wubi.exe with elevated permissions. Instead of double-click try with right-click, Run As Administrator.

Also I would recommend considering a proper dual install instead of wubi. wubi is more of a quick try, not recommended for long term install.

---

### Post by killer62491 on 2012-02-18
Well... ok so then back to my other question, is it possible to install/mount an ISO for installation use? if it is, Id like to know the method, because I don't currently have any cd-r's...... 
that and I've given up on using wubi after seeing that info 

thankee much!
.:ALPHA::HECTOR::SIERRA:.

---

### Post by killer62491 on 2012-02-18
oh and I'm not running Vista or 7, I'm running XP...
eh-heheh..... forgot to put that in there.....its a 6 yr old desktop, and ive been spicing it up hardware-wise, and now I'm on the OS and other software.

---

### Post by HeroOfCanton on 2012-02-18
You can install from a flash drive assuming your computer supports booting to one.  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by ottosykora on 2012-02-19
>Also, is it possible to somehow mount an ISO file of the disc image for Ubuntu installations?<

In fact wubi does something like that, but ending with all disks etc virtual as it can not do any real manipulations on the hard drive while the other os is running.

well think about it:
to mount an iso, you need to run an operating system, this will be your xp and some program running on top of that and this should install linux?




no, it does not work this way, it is rather so that from the CD or bootable usb the linux is started in a way that it is able form there to format partitions to linux specs and install boot manager and similar 'low level' tasks.

---

