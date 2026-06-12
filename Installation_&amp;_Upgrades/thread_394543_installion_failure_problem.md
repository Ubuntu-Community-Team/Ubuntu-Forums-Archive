---
title: "installion failure problem"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by bossmanx9 on 2007-03-27
Hi.  I've been trying to install Ubuntu 6.10 on one of my computers but it hasn't been working.  I downloaded the CD image from the website and burned it to a CD.  My computer boots from the CD, but then starts acting weird.  It brings up the loading screen where it shows the window manager and nautilus loading.  Then it brings up the desktop, but there's no mouse cursor and the screen starts to flicker.  Then it goes to a login screen and logs in automatically as "ubuntu."  Then it goes back to the loading screen, and does this all over again.  It loops through this over and over.

Eventually it stops doing this and leaves a window on the desktop.  I'm able to navigate through this and click on "Install."  The installation always fails on the 2nd step, however.  It brings up the world map, and when this comes up the mouse always freezes and the screen starts to flicker again.  After a minute it goes back to the login screen and starts all over.  I have tried many times, but this always happens and I have never been able to get through all the steps of the install before it crashes and restarts.

Any ideas?

---

### Post by tommcd on 2007-03-27
First, did you burn the iso at a very sloww speed? You might try burning the disk again at a slow speed to rule out a bad disk.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Also check the md5sum of the downloaded iso, and check the disk for defects if you can from the boot up screen:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If the disk turns out to be ok, then post your PC specs. You may need to install with some special boot parameters.

---

### Post by bossmanx9 on 2007-03-27
I checked the CD from the boot screen and it passed.  I also checked the md5sum and they matched.  I ran the memory test from the boot screen and didn't get any errors.

Here are my system specs:
AMD Athlon 650 MHz processor
20 GB Maxtor hard drive
256 MB RAM
Voodoo 5 5500 graphics card
Creative CD-RW disc drive

---

### Post by tommcd on 2007-03-28
Perhaps you could try the alternate CD. Go here:
[http://www.ubuntu.com/GetUbuntu/downloadmirrors](http://www.ubuntu.com/GetUbuntu/downloadmirrors)
Choose "other installation options" from a mirror near you. Scroll down to find "alternate CD" and choose the Intel PC (x86) version. It could be a problem with a graphics drivr I suppose. The alternate CD is a text based installer that may avoid a graphics issue.

---

### Post by bossmanx9 on 2007-04-03
Thanks for the help.  It did turn out to be a graphics problem.  I took out my Voodoo card and put in an even older video card, and now it works great.

---

