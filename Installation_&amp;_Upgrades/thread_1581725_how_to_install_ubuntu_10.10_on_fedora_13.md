---
title: "how to install ubuntu 10.10 on fedora 13"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by jim005 on 2010-09-25
Hi,

I am using only fedora 13 in my computer. Now i want install new ubuntu on fedora 13. i have downloaded iso from ubuntu and made cd, but i couldnt install it.. please help me..

jim005
:(

---

### Post by wojox on 2010-09-25
Why couldn't you install it? Did you boot off of the cd?

---

### Post by efflandt on 2010-09-25
You could boot to a live system from a CD and use System > Adminstration > Gparted to delete partitions before installing.

Or if partition(s) are already the size you want them, just use the Advanced mode to manually select existing partitions, where to mount them (you need at least /), and whether to format them.  It will automatically pick up any existing swap partitions.

I just installed 64-bit 10.10 beta to a USB hard drive.  Be prepared for some time the first time it does updates.  Mine said it could only do "partial" updates.  It uninstalled 2 packages and installed 491 of them.  But when I checked after that there were no new updates.

10.10 release version is due out Oct 10,

---

### Post by saifo1999 on 2011-03-10
how can i make it on a USB stick

---

