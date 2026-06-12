---
title: "Netbook Install Problem"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by ScottyExpress on 2010-10-12
I installed 10.04 from a thumbdrive on a HP Mini 5102 netbook that originally had Win7 Starter on it.  Everything went smoothly (after installing the proprietary wireless drivers), but now the darn thing doesn't boot at all unless I have the thumbdrive attached.  I'm assuming Grub got put on the thumbdrive instead of the netbook's hard drive, but how do i fix this?  Any help would be greatly appreciated!

Scotty
[http://www.scottyexpress.com](http://www.scottyexpress.com)

---

### Post by hecatae on 2010-10-12
I ran ```
sudo dpkg-reconfigure grub-pc
``` to fix the same issue by opening a terminal after booting with the usb drive inserted

---

### Post by ScottyExpress on 2010-10-12
Thanks, I'll give that a try!

---

### Post by hecatae on 2010-10-13
did it work?

---

