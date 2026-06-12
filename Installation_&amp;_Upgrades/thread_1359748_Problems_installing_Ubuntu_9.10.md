---
title: "Problems installing Ubuntu 9.10"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by perek on 2009-12-20
Hello,

I'm trying to install Ubuntu 9.10 from a CD or flash drive but always receive the error 'Operating System not found' when booting from CD or flash drive.  What am I missing, do I need to format the hard drive first?  It's brand new.  Thanks in advance.

---

### Post by lmarmisa on 2009-12-20
Check if the CD/DVD drive is defined as a boot device in your BIOS menu. I would define this device as the highest priority.

Best regards,

Luis

---

### Post by james2b on 2009-12-20
Try pressing your F key for the boot order menu, mine is F10, and some are F12, (Dell's) and others use F8 to get this boot menu. Then just arrow key down to your device, CD-DVD or USB, and then hit enter. Also it may help to first prepare that new hard drive by booting to a partition tool such as this Linux based GParted found here; [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

---

