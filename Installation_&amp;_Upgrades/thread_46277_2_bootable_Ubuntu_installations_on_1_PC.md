---
title: "2 bootable Ubuntu installations on 1 PC"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by slow learner on 2005-07-04
Hi

I initially installed Ubuntu on an old 8gig hdd using the default root file structure. (There is no other OS on this drive.)

I then installed XP on a 200gig hdd, and created the partitions listed below on each of the two 200gig HDD's.

At this stage my PC was setup like this:
All HDDs are ATA100   (PATA)
Partitions on the two 200gig HDD's were created with Partition Magic 8.05

IDE channels
Prim Master -   200gig  HDD (partitioning:    WinXP(NTSF bootable)130gig, Ubuntu(EXT2)60gig )
Prim Slave  -    Lite-on DVD burner

Secondary Master -  200gig HDD (partitioning:  Storage only 100gig NTSF,  storage only 90gig EXT2 )
Secondary Slave -  8gig HDD  Ubuntu (bootable)  


Ubuntu was installed last on the primary master HDD so as to enable multi-boot.
(the bios is set to boot to this hard drive)

After the install of ubuntu on this hard drive i can no longer boot to the 8gig HDD. (both were setup using the default  root file structure) 

Can someone please help me to modify my setup so i can boot to the Ubuntu 8gig HDD, and to mount the 8gig HDD in the Ubuntu installation on the primary master HDD (200gig).

I can mount the XP NTSF partition in ubuntu, but i haven't been able to mount Ubuntu on the 8gig HDD.


Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext2    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


and here is my menu.1st :


## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd1.
title		Ubuntu, kernel 2.6.10-5-686 (on /dev/hdd1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd1.
title		Ubuntu, kernel 2.6.10-5-686 (recovery mode) (on /dev/hdd1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd1.
title		Ubuntu, kernel memtest86+ (on /dev/hdd1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1



thanks for all help

---

### Post by kamstrup on 2005-07-04
It looks like your 8gig Ubuntu partition sits on /dev/hdd1. Adding this line:```
/dev/hdd1 /media/my_other_ubuntu ext2 defaults,user  0  0
``` to fstab should mount the partition on boot. Note that you need to create the directory /media/my_other_ubuntu...

You can mount the volume right away with "sudo mount /media/my_other_ubuntu".

PS: Are you sure that you have ext2 and not ext3 partitions? If so try changing the above ext2 to ext3 and do the "sudo mount /media/my_other_ubuntu" again (you might need to umount it first...).

Good luck!

---

### Post by mingus on 2005-07-04
Is Ubuntu on HDD1 in a logical partition inside an extended?  Where is the swap partition?  And on the 8GB drive, is there a swap as ref'd in fstab?  Perhaps it would help if you posted your entire partition table (fdisk -l).

---

### Post by slow learner on 2005-07-05
Thanks kamstrup I got it sorted out :)

I mounted the 8gig drive and edited the fstab file and now it can boot in. I have just unpluged the drive as a back up if something goes wrong.

@ Mingus,
hi -  I installed directly to the 8gig drive and let ubuntu handle the partitioning & formatting. I'm not sure what the 'default' would be.

---

