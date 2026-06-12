---
title: "New 7.04 Install: grub-install (hd0) failed"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by guylan1975 on 2007-04-22
Hey,

I am installing a fresh installation of 7.04 on partition 5 without swap space and am getting the above error message in the GUI installer. The other partitions contain XP.

When I look at the message log I see the following errors: 
The file boot/grub/stage1 not read correctly.
error: Running 'grub-install  --no-floppy "(hd0)"' failed.

I have tried 3 times and after the third time I tried running grub-install manually without success (thinking this was probably the last step in the install process)
I even tried running grub and going through the manual process of setting it up.

I have a dell XPS laptop.

Any ideas would be greatly appreciated...

---

### Post by pepsi_max2k on 2007-04-22
what's in /etc/fstab? and have you tried changing the boot loader device option (last step of live install, advanced button) to any of these?

---

