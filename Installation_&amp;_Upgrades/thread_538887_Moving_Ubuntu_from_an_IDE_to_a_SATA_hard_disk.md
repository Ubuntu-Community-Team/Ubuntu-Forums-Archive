---
title: "Moving Ubuntu from an IDE to a SATA hard disk"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by chipper_30 on 2007-08-30
Hello,

Here is my current setup:
1) hda has XP
2) hdb has ubuntu, the swap partition, and a fat32 partition that I use to move files between the 2 OSs.

I believe grub is starting from hda.
Now I have new SATA disk and I would like to replace hdb with this new disk.

At the moment I have all 3 disks plugged in, but I would like to remove hdb. In XP I have copied the partitions from hdb to the new disk (using partition suite). XP and ubuntu start fine, but I'm pretty sure that ubuntu still starts from hda2.
I believe I need to make some changes in /boot/grubmenu.lst, and I have however read about UUIDs in fstab... and have not figured out if I should do something in there, can anyone help me out with that?

Thanks!

---

### Post by chipper_30 on 2007-08-30
OK, I changed fstab with the UUIDs of the new partitions (except the swap which didn't have any so I used the dev/ name). Then grub/device.map to change hd1 to the new (sda) disk. Then finally grub/menu.lst with the UUIDs of the new partitions.
I've unplugged my old HD and everything seems ok :-)

---

