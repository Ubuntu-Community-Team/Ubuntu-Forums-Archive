---
title: "Grub and error 17 again"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by chene on 2007-05-22
hi all,

I have decided to switch from OpenSuse 10.2 to Ubuntu 7.04 and now it seems to be a bad idea.  After installation Ubuntu 7.04 from live-cd, I ended with the common grub problem.  I seek you help.

Problem:  at boot up, Grub gives "error 17" and refuse to boot.

My system:

AMD64 with the following HD configurations:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       24321   195358401    f  W95 Ext'd (LBA)
/dev/hda5               1       24321   195358369+   c  W95 FAT32 (LBA)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/sda2            4845        4975     1052257+  82  Linux swap / Solaris
/dev/sda3            4976       30401   204234345    f  W95 Ext'd (LBA)
/dev/sda5            4976       30401   204234313+  83  Linux


I have Ubuntu 7.04 (and previously OpenSuse 10.2) installed in /dev/sda5.  If I mount /dev/sda5, the grub files are:
 
menu.lst:

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=117806c0-8c05-44ae-8ddd-d00c66015414 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=117806c0-8c05-44ae-8ddd-d00c66015414 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,4)
kernel          /boot/memtest86+.bin
quiet

my /etc/fstab is:
root@ubuntu:/mnt/test/boot/grub# cat ../../etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=117806c0-8c05-44ae-8ddd-d00c66015414 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4582-0A2A  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=A624485B2448309B /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=34028d5e-1c84-404d-9d48-da405a813e36 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I have tried various grub trick including booting with live-cd and run grub command, etc.  I've also re-install ubunto 7.04 from the life CD, each time changing the grub options between (hd0) and (hd1).  None of these helped.  

Can someone please give me some idea of what went wrong and how I might solve it?  If nothing works, I guess I have to switch back to OpenSuse which I know will work.

Thank you,

---

### Post by siralphred on 2007-05-22
try reinstalling grub through this guide [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by confused57 on 2007-05-23
Here's another possible solution:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by chene on 2007-05-23
hi all,

I *kinda* solved this problem but encountered another grub-related problem.  As indicated in my original post, I have a PATA (which I used as a data drive) and a SATA drive.  The SATA is the first-bootable drive in the BIOS and it houses both winxp (sda1) and linux (sda3).

I solved the grub error 17 problem by disconnecting my PATA drive and installed ubunto with only SATA drive powered on.  This works wonders as now I have a fully functional system.  The problem is, if I re-attach the PATA drive I ended up with a "grub error 22"!

how can I solve this problem?

please let me know,

thx,

---

### Post by confused57 on 2007-05-23
Not sure it'll help you, but here's a description of grub error 22:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22)

The only thing I can think of is to make sure your SATA drive is set in bios to boot before your PATA drive...I'm wondering if your PATA drive still has grub on the mbr from your previous Ubuntu install.

---

### Post by chene on 2007-05-23
the SATA is the first drive on the BIOS, that's why I was puzzled.  You may be right that there might be residual MBR records on the PATA drive, as I was pretty certain that I played with such GRUB options when I was trying to fix the grub error 17 problem using the live-cd.

problem is, with the computer not able to boot, can't really solve this problem.

any help is very much appreciated,

---

### Post by confused57 on 2007-05-23
> **chene said:**
> the SATA is the first drive on the BIOS, that's why I was puzzled.  You may be right that there might be residual MBR records on the PATA drive, as I was pretty certain that I played with such GRUB options when I was trying to fix the grub error 17 problem using the live-cd.

problem is, with the computer not able to boot, can't really solve this problem.

any help is very much appreciated,
If somehow your bios is still booting first to the PATA, there's not much you could do with the grub menu on it's mbr if it's your old install.  I suppose you could try to install grub to your PATA mbr, which won't hurt anything, but it'd be interesting if it gives you a different grub error.
Sounds like you already know how to reinstall grub with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

the command "find /boot/grub/stage1" will probably return "root (hd0,2)"...you could try "setup (hd0)" and also "setup (hd1)"...this might install grub to  mbr of both hard drives, which I don't believe will affect your system.

Then when you boot up your computer, and if you get a grub menu at boot, highlight your Ubuntu entry, press "e" then change root to (hd1,x) or whatever your root partition is, then press "b" to boot.

It's about all I can think of for you to try...

---

