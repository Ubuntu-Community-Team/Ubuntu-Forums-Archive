---
title: "Graphical Interface Problem"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by bradhawk08 on 2006-02-21
Ok, so i installed Ubuntu on my master hard drive using the automatic resize partitioner.  It ran through the installation correctly and rebooted and started up Ubuntu, but then it gave me the following error:

> Failed to start the X server (your graphical interface) it is likely that it is not setup correctly. Would you like to view server output to diagnose the problem?

Clicking 'YES' it brought up the following page:

> X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build OS Linux 2.6.10 i686 [ELF]
Current OS Linux bjdowns 2.6.12-9-386 #1 Monday October 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
     Before reporting, check [http://wiki.X.org](http://wiki.X.org) to make sure you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera)(gcc version 3.4.5 20050809(PreRelease)(Ubuntu 3.4.4-6ubuntu))
#1 Monday October 12 13:14:36 BST 2005
Markers: (--) probed, (**)from config file, (==)default setting

if anyone has a solution please post... thanks!!
Brad

---

### Post by mustang on 2006-02-21
Try

```
 sudo dpkg-reconfigure xserver-xorg
```

Let us know how it goes!

---

### Post by souteneur3190 on 2006-02-21
are u on the same computer that this happend to?  If your not than reinstall ubuntu...ur screwed

---

### Post by bradhawk08 on 2006-02-22
So i went onto that site that the error told me to go to.  They have a new release. My computer (aka the current Ubuntu release) has 6.8.2 and they have released a 6.9.0 and a 7.0.  Upgrading would fix the problem because it adds drivers for ATI Radeon cards.  The problem is is that i'm having trouble interpreting their instructions on how to upload and upgrade the system. can anyone help?

---

