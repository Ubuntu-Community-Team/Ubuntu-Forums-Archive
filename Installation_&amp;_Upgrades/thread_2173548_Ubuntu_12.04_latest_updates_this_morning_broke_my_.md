---
title: "Ubuntu 12.04 latest updates this morning broke my system"
date: 2013-09-10
forum: Installation &amp; Upgrades
---

### Post by theDentist on 2013-09-10
Hi all,

I installed the latest updates, the usual way, this morning, this included an updated kernel and I noticed an nVidia graphics driver update. On reboot the system had two faults. My splash screen was black and I had "xubuntu 12.04" text in it.  I have never installed any xubuntu stuff on this machine, so where that came from is a mystery. The second major problem is I got only the command prompt. the graphical desktop was broken.  So I rebooted into the previous version (recovery mode failed) and managed to get a graphical desktop. Suspecting that driver update was the culprit, I looked at the driver situation.  I noticed the currently installed version was an post-release updated 304 driver.  So I installed a listed 319 instead.  That did the trick and I was then able to boot into a desktop without going into a "previous version" in the grub menu (I presume I'm with the latest kernel).  But I am still stuck with the xubuntu splash screen (black backgroung).  I have deleted all links to xubuntu splash screen and text in /lib/plymouth/themes/default.plymouth, that where present but made no difference.  Any ideas anyone how to fix all this. I have a feeling more of the system was affected then is obvious.

Peter

---

### Post by theDentist on 2013-09-10
Just solved the splash screen problem with the help of this thread  
                [http://askubuntu.com/questions/129218/how-to-return-the-login-screen-to-the-default](http://askubuntu.com/questions/129218/how-to-return-the-login-screen-to-the-default)

But I'm getting error messages, during boot that drops me out into verbose mode, they as passing way to quick for me to study them accurately, I can still boot into normal desktop OK

Peter

---

### Post by theDentist on 2013-09-10
Oh my kernel version is 3.2.0-53-generic-pae

---

