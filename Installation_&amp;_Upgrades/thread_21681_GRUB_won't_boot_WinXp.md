---
title: "GRUB won't boot WinXp"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by andrelll on 2005-03-23
Hi! I'm new to linux and today i decided to install ubuntu.

I have 2 hard drives, a 40gb one and a 120gb one. WinXP is installed on the 120 gb drive, and i installed ubuntu on the 40 gb drive. What happens is that when i choose to boot winxp, grub gives me an error message saying "Error while parsing number", which is error 23 i think.

Here's what fdisk -l looks like:
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4803    38580066   83  Linux
/dev/hdb2            4804        4865      498015    f  W95 Ext'd (LBA)
/dev/hdb5            4804        4865      497983+  82  Linux swap

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS
root@Joaquim:/home/andre # gedit /boot/grub/menu.lst


And /boot/grub/menu.lst looks like this:

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,0)
kernel		/boot/memtest86+.bin

title 		Windows install
rootnoverify 	(sd0,0)
makeactive
chainloader 	+1
boot

Can anyone help me? Unfortunately i really must boot winxp.

Thank you

---

