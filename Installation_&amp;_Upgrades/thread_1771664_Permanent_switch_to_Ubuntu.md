---
title: "Permanent switch to Ubuntu"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by flaptop on 2011-05-30
I had installed a partition along side windows7 with Ubuntu about a week ago to test it out. Now I decided to dedicate my system to Ubuntu. Is there a way to remove windows7 leaving just ubuntu as my main os? if not, how can i make a permanent switch? thanks. :)

---

### Post by sanderd17 on 2011-05-30
First: you did install a dual boot and not via Wubi did you?

Then just boot a live CD, delete the Windows partition (which is formatted as NTFS) with the Gparted application and resize the ubuntu partition to take the whole size.

Be aware that you will lose everything on your windows partition: if there are any files there that you want to keep, save theem somewhere else.

As a final warning: one week seems a bit early to know if you are ready. I would at least wait until the next version of Ubuntu comes out (in October).

---

### Post by lordadi on 2011-05-30
Well, if you want to get rid of M$, you should first backup all your data. After that re-install Ubuntu on the whole drive and that will wipe Windows completely. As far as I am aware, this is the only way of doing it.


Good luck!
----EDIT------
Follow sanderd17's method - that does not entail a full installation.

---

### Post by Andreawws on 2011-05-30
get Gparted (Live CD) and remove the windows partition(s)
then extend your ubuntu partition to use all the free space (It isn't hard, when you have booted into Gparted you can find it, more exactly right-click the ubuntu partition and extend it) ^^

[http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html](http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html)

that should help you on how to make a bootable usb....
prefer CD/DVD?

then use google (I do not really have time to find this for you)

EDIT:
Dammit, you guys beat me to it!

---

### Post by zzzz401 on 2011-05-30
Use a partitioning program (Gparted) and format the windows partition and use as free space for Ubuntu

---

### Post by donato roque on 2011-05-30
I just want to welcome you. 
And add to the excellent suggestions here- you might consider a separate partition for your /home, where you save all your personal data. Any changes you make to Ubuntu (such as upgrades) will leave your data untouched.

---

### Post by flaptop on 2011-05-30
thanks everyone for your help.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Here is a nice guide to Natty to walk you through the process of getting everything setup just right too, in case you need it:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Welcome to Ubuntu! :popcorn:

---

### Post by walt.smith1960 on 2011-05-31
Unless you need the disk space, you might consider shrinking your Windows partition but not  deleting it.  Don't put yourself in the position of some that have posted here lamenting about needing Windows for an oddball piece of software for which there is no equivalent in Linux and not being able to reinstall Windows.  Or needing to troubleshoot a piece of hardware and the manufacturer requires Windows to do so.   I way prefer Ubuntu over Windows and haven't used Windows in months but it doesn't  take that much disk space for me so I put Windows in the attic along with other unused claptrap.  I can bring it down if I need it.

---

