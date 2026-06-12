---
title: "Ubuntu 7.10 boots directly into grub"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by trackzilla on 2007-12-22
I'm attempting to dual boot my Thinkpad T61 and ran into this problem.  I have the following SATA drive setup:

sda1 = hidden IBM recovery partition
sda2 = Vista Ultimate
sda3 = swap
sda4 = Ubuntu 7.10

Not wanting to overwrite the Vista MBR, I installed grub to hda0,3; which should be my Ubuntu partition.  I booted back into Vista and installed EasyBCD, added the Ubuntu partition to the boot loader and can successfully see both boot options when my Thinkpad reboots.

Here is my problem, when I select Ubuntu 7.10 to boot, I am immediately taken to a grub> command, never booting into Ubuntu completely.  Anybody know how to fix grub so that I boot directly into Ubuntu?

---

### Post by meierfra on 2007-12-22
I need some information to help you. At the grub prompt type:

find /boot/grub/menu.lst

and  post the output.

Also boot from the ubuntu Live CD, open a terminal (Applications->Accessories->Terminal)
and post the out of 

```
sudo fdisk -lu
```

and 

```

mkdir ubuntu
sudo mount -t ext3 /dev/sda4 ubuntu
cat ubuntu/boot/grub/menu.lst
```

---

### Post by trackzilla on 2007-12-22
OK:

grub> find /boot/grub/menu.lst

[INDENT]Error 17: File not found[/INDENT]

sudo fdisk -lu

[INDENT]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e2807b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    10149887     5073920   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    10149888   261378047   125614080    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       261379440   263420639     1020600   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda4       263420640   312575759    24577560   83  Linux
Partition 4 does not end on cylinder boundary.[/INDENT]

mkdir ubuntu
sudo mount -t ext3 /dev/sda4 ubuntu
[INDENT]
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/INDENT]

When I formatted my ubuntu partition I chose reiserFS instead of Ext3 if that helps.

---

### Post by meierfra on 2007-12-22
try

```
sudo mount -t reiserfs /dev/sda4 ubuntu
```

and/or
```
sudo mount  /dev/sda4 ubuntu
```

---

### Post by trackzilla on 2007-12-22
cat ubuntu/boot/grub/menu.lst

[INDENT]cat: ubuntu/boot/grub/menu.lst: No such file or directory[/INDENT]

---

### Post by Pumalite on 2007-12-22
I think you might have a Partitions Table problem. Check your drive with TestDisk: 
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
And fix it if you need to.

---

### Post by trackzilla on 2007-12-22
I'm not sure I need to test the disk, this is a clean install.  It appears that the Ubuntu operating system files are on the drive and there are other files in the /boot/grub folder, just not the menu.lst

---

### Post by meierfra on 2007-12-22
Did you get any error messages when you installed grub?

---

### Post by meierfra on 2007-12-22
Didn't need see your last post. Maybe you just need to generate menu.lst. Give me a few minutes to write up instructions.

---

### Post by trackzilla on 2007-12-22
Thanks, I really appreciate your help.

---

### Post by meierfra on 2007-12-22
This should generate menu.lst

```
sudo mkdir  /ubuntu
sudo mount -t reiserfs /dev/sda4 /ubuntu
sudo mount -t proc none /ubuntu/proc
sudo mount -o bind /dev /ubuntu/dev
sudo chroot /ubuntu
sudo update-grub
exit
```

---

### Post by trackzilla on 2007-12-22
Thank you for all your help; it worked!

---

### Post by meierfra on 2007-12-22
It  worked as in "it generated menu.lst" or as in "I booted successfully into ubuntu"?

---

### Post by trackzilla on 2007-12-22
It worked = created menu.lst and booted into Ubuntu.  Thank you again.  I was having a problem earlier with the Thinkpad/Lenovo AHCI/Compatability mode ******** regarding my SATA drive.  Once I put the drive in compatability mode and everything works fine.  Ubuntu will boot up, shut down, and reboot.  Thanks again!

---

