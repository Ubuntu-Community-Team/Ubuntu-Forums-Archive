---
title: "Server install + ubuntu-desktop == Desktop install?"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by nightmarestreet on 2008-09-18
Hey lads,

I've got a Ubuntu server set up with full disk cryptography, and I'm looking to do the same to my laptop.

I noticed that the standard installer does not have the LVM/encryption option. And I heard that the alternate cd does strange things (for example, installs lilo instead of grub).

My question is this: if I install from the server cd, and then aptitude install ubuntu-desktop, will that pull down everything that gets installed from the desktop cd? Will I still get the graphical boot menu?

Cheers!

---

### Post by Linteg on 2008-09-18
I've installed from the alternate CD many times (I use LVM) and it has never installed lilo (by default) or done anything weird. In fact, I'm certain it is the same installer as Ubuntu Server but with (more or less) the same set of default packages as the normal desktop install.
More on topic: Yes, ubuntu-desktop should install all the packages included in the normal desktop install, although you would still have all server packages (apache, mysql, php etc) installed.

---

### Post by vorgusa on 2008-09-18
Same here, I have never experienced and issue with the alternative CD.  Give it a try it can't hurt to see what happens.

---

### Post by nightmarestreet on 2008-09-19
Hey thanks for the info guys.

I think I'll go with the server install -- having the server packages installed seems like it would only be a good thing.

Cheers.

---

