---
title: "[SOLVED] grub problem error 22"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by graham45 on 2008-06-28
Hi  I am assisting a friend install ubuntu (8.04)  and all is well until the dual boot setup (grub) stage is reached.  His system consists of 2 disks. XP is on disk 0 and the other drive is a 300gb NTFS drive (data only). From the live CD perspective the order of the drives is reversed I think.  I have tried the grub fix and the find command says hd(1,1)is the linux partition. So I install on this basis and the system reboots to the grub menu OK, but either XP or Ubuntu selection has errors.  error 22 for linux and I cant recall the error for XP but cant find file (or similar).  I have recovered his windows setup with a fixmbr command for the moment.  I am puzzled as to what grub is doing at this point !  I am thinking to remove confusion disconnect his internal data disk perhaps ! disk 0 setup (disk 1 to grub) is 3 partitions, 0 is XP system,  1 is ubuntu (jfs) and 2 is swap !  Does anybody have some suggestions please ?  First time on this forum so apologies if I am in the wrong area or something?

---

### Post by Pumalite on 2008-06-28
If you can boot a Live CD; post:
sudo fdisk -lu

---

### Post by lswest on 2008-06-28
What I used to do was change (in the BIOS) the order of the drives so Ubuntu's drive is the first drive, then installed GRUB to (hd0), and that works fine, best part is if it breaks, just change the order of the drives for Windows to boot normally.

---

### Post by graham45 on 2008-06-28
> **lswest said:**
> What I used to do was change (in the BIOS) the order of the drives so Ubuntu's drive is the first drive, then installed GRUB to (hd0), and that works fine, best part is if it breaks, just change the order of the drives for Windows to boot normally.
Yes, thanks for the BIOS suggestion !  The windows/ubuntu drive (SATA) is the default in the BIOS.  The second drive is an IDE and is connected to a RAID socket, but this has no XP or Ubuntu installation at all. I am organising an fdisk -lu  output to clarify the order of the 2 disks.  Thanks !

---

### Post by graham45 on 2008-07-04
The output from fdisk -lu is as follows .....note that the 80gb drive is the default boot drive for windows etc and the 320 gb drive is an ide on the raid controller which is not visible at the set boot disk level....

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009b72a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa91fa91f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   115346699    57673318+   7  HPFS/NTFS
/dev/sdc2       115346700   148103234    16378267+  83  Linux
/dev/sdc3       148103235   156296384     4096575   82  Linux swap / Solaris

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe93a112c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   781401599   390700768+   c  W95 FAT32 (LBA)

---

### Post by Pumalite on 2008-07-04
Which one is SATA and which IDE?

---

### Post by graham45 on 2008-07-04
The sata is the 80 gb drive (/dev/sdc) and the 320gb drive is the IDE (/dev/sda - on a raid controller socket).  I reckon this order is the opposite to the general system state !

---

### Post by Pumalite on 2008-07-04
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by graham45 on 2008-07-04
Yes , indeed , I have used this procedure to reinstall Grub - but that is when I reboot and get a menu from grub OK, (which looks promising)  but when I select ubuntu i get error 22.  When I select windows I get some file not found error.

---

### Post by graham45 on 2008-07-04
Any merit in disconnecting the IDE drive do you think (as its unimportant to the boot process) - it may help grub perhaps ?

---

### Post by Pumalite on 2008-07-04
At the Grub menu, outline Ubuntu and hit 'e' and 'e' again to edit boot
 At:
grub>try different combinations until you hit the right one and then go edit menu.lst.

---

### Post by graham45 on 2008-07-04
Yes, thanks for that suggestion.  grub can find the menu OK but I think from there its confused as to the correct settings, so if I can edit grub with your recommended procedure we may get somewhere !  Its very late at night here and I shall give this a try tomorrow afternoon.  By the way my Ubuntu is working very well !  Thanks again.

---

### Post by graham45 on 2008-07-05
Yes, I thank you for your assistance. It was spot on. For some strange reason the find command in grub found the right part for /boot/grub/menu.lst but then was pointing to the wrong drive for the kernel and the same for windows.  The E command worked as it should and allowed me to permanently edit the menu.lst (and remove a couple of map settings on the windows boot section which were causing problems too. Its all working well now.  I understand the process well now too.  Well done and I appreciate your time.

---

### Post by Pumalite on 2008-07-05
You are welcome. Good luck!

---

