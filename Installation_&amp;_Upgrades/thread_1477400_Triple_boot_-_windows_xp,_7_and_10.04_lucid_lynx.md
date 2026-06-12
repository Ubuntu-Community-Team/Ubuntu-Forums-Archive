---
title: "Triple boot - windows xp, 7 and 10.04 lucid lynx"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by fagath on 2010-05-08
This is to share my experience with this triple boot setup in a hasee laptop.
1 install windows  xp
2 boot with lucid live usb/cd and create a ntfs partition with gparted for windows 7 (i used 90 gb for win xp and 30 for win 7)
3 install windows 7 in the new partition using the custom option of the installer. now windows 7 bootloader takes over
4 boot with ubuntu live usb/cd and using gparted create manually the partitions for ubuntu. The plan is to tell ubuntu not to install grub 2 in mbr but install it in ubuntu's partition. The partitions needed is a third partition for swap (I used 512 mb) and a forth ext4 partition for ubuntu. (I resized win 7 from 30 to 20 and left approx 10 gb's for swap and ext4)
5 install ubuntu using the manual option where you need to point the installer to the new ext4 partition (remember to check the format option) and of course in the advanced button you need to tell the installer to put the boot loader in ubuntu's partition
6 reboot and you find again win7 bootloader and not grub
7 boot in win 7 , download and install easybcd 1.7.2
8 open easybcd and create a new menu entry where you name it ubuntu and point to ubuntu's partition. you are done.
9 optionally rename "older versions of windows" to windows xp using easybcd
10 also optionally in ubuntu install startup manager and change boot time to 0 in order to skip grub's wait time

the result is a system with xp, 7 and lucid using the win 7 bootloader
note that selecting ubuntu opens grub from ubuntu's partition.

I ended using this combination because at my first attempt I let grub install in mbr. The result was that the system booted to grub where the last option was windows 7 loader. That led to another menu with "earlier versions of windows" and win 7. Given that for that machine the main os is xp this setup was sub-optimal.

Any feedback would be appreciated-good luck
PS Has anybody used grub 2 to boot directly to these three os?

---

### Post by oldfred on 2010-05-08
Both window have to be in primary partitions or it gets real complex.

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

