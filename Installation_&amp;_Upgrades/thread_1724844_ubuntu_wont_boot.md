---
title: "ubuntu wont boot"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by Bluestars on 2011-04-08
I just used usb to install ubuntu 11.04 next to Ubuntu.  Now when I boot it asks me if I want to boot Windows 7 or Ubuntu.  If I select windows 7 it boots fine.  If I select Ubuntu it gives me this message instead of a list of kernels to choose.

It says windows has failed to start. this may be due to a recent software or hardware change. insert your windows disc and run windows repair.

File: Ubuntu\winboot\wubildr.mbr

status: 0x0000225

Will not load due to the application being missing or corrupt.

---

### Post by bubbajtj on 2011-04-08
So did you select windows 7 when the kernals popped up or did you select ubuntu 11.4 (not safe mode)?

---

### Post by Bluestars on 2011-04-08
> **bubbajtj said:**
> So did you select windows 7 when the kernals popped up or did you select ubuntu 11.4 (not safe mode)?

Well normally it asks if i want to boot windows 7 or ubuntu.  If I pick Windows 7 it boots up.  If I chose Ubuntu it would then list kernels to choose and then boot into Ubuntu.

Now when I click Ubuntu, instead of showing me the list of kernels it just shows the error I posted above.  Then I can go back, and pick windows or reboot.

I selected windows and am on windows 7 right now.

---

### Post by Hedgehog1 on 2011-04-08
> **Bluestars said:**
> It says windows has failed to start. this may be due to a recent software or hardware change. insert your windows disc and run windows repair.

File: Ubuntu\winboot\**wubi**ldr.mbr

status: 0x0000225

Will not load due to the application being missing or corrupt.

Bluestars,

The Natty Beta had a bug that kept it from installing properly for **wubi** installs.   It appears that your install was affected by this bug.  I do not knows if that issue is resolved yet.

If you wish to be part of the beta testing efforts for Natty, you will likely need to do a traditional dual boot install.


***The Hedge***

:KS

---

