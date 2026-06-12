---
title: "Recent updates made me crazy."
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by mayday73 on 2007-09-04
I have two computers and recently  installed Windows XP and Ubuntu 7.04 on first one and Windows XP and Ubuntu 7.04 - Alternate on the other one. They had been running without special problems but many problems occurred after updating. The second one with Ubuntu 7.04 - Alternate did not even boot. :mad:  I suspect that it might be caused by kernel upgrade. Some say that Linux is stable but I have always been afraid when updating or installing new softwares. I think that Linux desktop distributions are not so stable at least.

---

### Post by Pumalite on 2007-09-04
Updates tend to change settings in your menu.lst.
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by merlinus on 2007-09-04
Your linux root may have changed as a result of the recent kernel update.

If you press e at the grub menu, you can see what the root is.  If you have one hdd and ubuntu is on the second partition, then it should be (hd0,1).

When you get it working, you can edit /boot/grub/menu.lst to make the change permanent.

Of course, your problem may be something else entirely....

-merlin

---

### Post by keayz on 2007-09-05
A slightly different problem after update on 2 September. I now cannot access the Internet on my 2.6.20-16 kernel, though the 2.6.17-11 kernel works perfectly. I assume the kernel has been modified and is no longer supporting something (I'm a newbie).

---

