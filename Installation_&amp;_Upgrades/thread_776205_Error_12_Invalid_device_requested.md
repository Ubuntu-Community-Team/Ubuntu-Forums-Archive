---
title: "Error 12: Invalid device requested"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by ondrisko on 2008-04-30
Hello, I'd appreciate very much any help with this problem:

I installed new Xubuntu 8.04 on a computer with Windows XP already installed. Now when I try to boot Windows, I get following error:
> Error 12: Invalid device requested 

My sudo fdisk -l:

> 
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        7296    58605088+   f  W95 Ext'd (LBA)
/dev/sda5            1021        5483    35841928+   7  HPFS/NTFS
/dev/sda6            5483        7296    14560528+   7  HPFS/NTFS
/dev/sda7             896        1020     1003999+  82  Linux swap / Solaris
/dev/sda8               1         895     7188993   83  Linux

Partition table entries are not in disk order


My /boot/grub/menu.lst (bottom part):

> 
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fec1c917-76b1-46bd-b5a5-bb940dbba967 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fec1c917-76b1-46bd-b5a5-bb940dbba967 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


Thank you very much for any help...

---

### Post by Herman on 2008-04-30
You need to use a partition editor to set your boot flag in the logical partition and delete or comment out the 'makeactive' command from GRUB's /boot/grub/menu.lst file.

Check to see if you have the three vital Windows boot loader files present in the root of your Windows drive, ntldr, ntdetect.com and boot.ini. 
If not you can boot Windows for now with the CD you can download from ' [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm") ' by Miles Comer, until you can get more help with your problem.

Regards, Herman :)

---

