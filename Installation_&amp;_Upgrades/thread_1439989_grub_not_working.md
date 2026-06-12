---
title: "grub not working"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by dbowlin17 on 2010-03-26
I had installed ubuntu, then windows xp, surprise surprise i lost the boot loader for ubuntu. i have 2 different live boot cd's one for 9.10 and another for 10.04. my pc would be running 10.04, if i could install grub. When i go to help on the live boot disk menu, it tells me that rescuing a broken system is not enabled on either disk, though i downloaded a full copy of the disk when i downloaded it. What can I do to get grub back onto my computer? I deleted the XP partition hoping that would help. it didn't now the pc will only boot when i have the live boot cd. help!!!

---

### Post by andrewthomas on 2010-03-27
Cut the code and paste it into the terminal and post the output :
```
sudo fdisk -l
```
from what you say you should only have 2 partitions left but just to be safe.

---

### Post by oldfred on 2010-03-27
The reinstall is not from the CD. The CD is used just to boot and you either chroot into the system to install old grub or mount the hard drive partition for new grub2. The install is actually using the grub from the install on the hard drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by dbowlin17 on 2010-03-27
i got it. dunno how but i did thanks.

---

