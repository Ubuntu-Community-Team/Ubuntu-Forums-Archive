---
title: "Weird partition issue"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by The Mad Scientist on 2006-06-25
I recently installed Windows Vista on an open space on my hard drive I had reserved for the purpose.  As expected, it wiped my MBR, and I have fixed that problem.  However, the open space was before my Ubuntu 6.06 installation, so the act of creating a new partition and installing bumped Ubuntu from /dev/hda1 to /dev/hda2.  I fixed mtab, fstab and grub's menu, but there is still something missing.  When I try to boot, it finds the linux kernel and starts to boot it, but still tries to mount /dev/hda1, finally quitting, after several mount errors, while trying to initialize tty.

Any ideas on where the problem is?  I think I have just missed one or two initialization files.

---

### Post by jasutton on 2006-06-26
Make sure you edited /boot/grub/menu.lst properly.  In particular, make sure it says "root=/dev/hda2" on the kernel parameters.

Also, if you haven't already done so, make sure you have edited /etc/fstab appropriately. :)

---

### Post by The Mad Scientist on 2006-06-26
Had done fstab.  Fixed the automagic kernel parameters in menu.lst.  Still the same problem.  Any more ideas?

---

### Post by jasutton on 2006-06-27
Well, you might want to try re-installing GRUB.  This can be done by booting off a live cd of some kind and chrooting into your root partition (in this case where ever you mount /dev/hda2), and then running "grub-install /dev/hda" to reinstall grub properly.  If that doesn't work, I'm probably fresh out of ideas...

---

### Post by The Mad Scientist on 2006-06-27
I had missed a couple of things in the GRUB menu.lst.  Fixed those.  Now I get further.  It actually boots, but device driver load fails.  It then dumps me into terminal mode login, but if I try, it just crashes with a couple of screens of repeated error message.

I tried doing a grep of the entire disk looking for "hda1" using the live CD, but it halted without finding anything.](*,) 

Anyone know what script is run at login?  I can try looking through that.  Other than that, it appears I may have to reinstall Ubuntu, and I was really trying to avoid that.

---

