---
title: "problem while dual booting vista and ubuntu"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by elect82 on 2008-08-20
I have installed  ubuntu with vista already installed and it has installed linux on main drive on which vista installed and format whole disk instead of another free 14 GB drive partition and i lost all my data. then from live cd i had recovered all data lost due to formatting and removed ubuntu which was previously installed. then i restart and it showed error in grub as it was already deleted. now i want to use my previous setting with vista but it couldn't boot up with vista. i try to use start up repair but it shows that there is some removable usb connected and it needs to removed but actually there was no device conneted. then i try to installed linux again from live cd. before that i have used Gparted and make partition of 10 GB and try to installed but it says that no valid space. then i have another 14 GB partition
which i formatted in nfts format and try to install but error message come like root menu not defined and go to partition editor but there is no such option. i tried all option like creating another partition with ext2/3 etc. but nothing works. now i can't use vista or ubuntu. can anybody help me to go back to vista and use my original setting. i have try to restore original point for
vista but no help. i thought that ubuntu is easy and friendly system but i was wrong.

---

### Post by manishtech on 2008-08-20
> i thought that ubuntu is easy and friendly system but i was wrong
Ubuntu is still user friendly, only thing required is that installation should be done properly. You must have selected the option "Use Entire Disk " during installation. This is the reason why the whole disk was formatted.

You should have tried manually creating a root and swap partition and mounting them. This may be a bit tough I agree, but safe and secure since you know which partition is being altered.

Can you boot in LiveCD and give us the partition layout using the command



> sudo fdisk -l

this l is small 'L'


Am not arrogant or harsh, dont take me wrong.

---

### Post by manishtech on 2008-08-20
a

---

### Post by elect82 on 2008-08-20
thanks for reply
As u said to me i type that command and i have pasted disk information below
-------------------------------------------------------------
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           17324       19130    14514727+   5  Extended
/dev/sda2   *        1316       17323   128574452+   7  HPFS/NTFS
/dev/sda4           19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda5           17324       18748    11446281    7  HPFS/NTFS
/dev/sda6           18749       19003     2048256   83  Linux
/dev/sda7           19004       19130     1020096   82  Linux swap / Solaris

Partition table entries are not in disk order
--------------------------------------------------------

I was trying to install on sda5 but it gives error that root menu not found and for guided it shows option to install only on 122 GB (sda2) main drive.

---

### Post by caljohnsmith on 2008-08-20
> **elect82 said:**
> can anybody help me to go back to vista and use my original setting. i have try to restore original point for
vista but no help. i thought that ubuntu is easy and friendly system but i was wrong.
If you just want to go back to Vista and are sure you don't want Ubuntu, you can use [this guide to restore the Vista master boot record (MBR)]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD"); if your partitioning is not too messed up at this point, then reinstalling the Vista MBR should allow you to boot directly into Vista again.

---

### Post by manishtech on 2008-08-20
I think you have lots of unallocated space...

---

