---
title: "Preparing flash drive for encrypted Ubuntu installation"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by cashmank on 2012-02-23
Hi all, I am installing Ubuntu on a flash drive with LUKS encryption  using the alternative CD. I'm confused as to whether I need to  prepare/partition the flash drive beforehand. 

I have been generally following the guide [Ubuntu Encrypted Flash Memory Installation]("http://members.iinet.net/%7Eherman546/p19.html") and Method 1 of [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"). 

When I get to the part to install GRUB, I try to install it on the first  USB partition (i.e. /dev/sdb1) but the only partition it will install  on is /dev/sdb.

Am I missing something here?

---

### Post by Herman on 2012-02-24
> I'm confused as to whether I need to  prepare/partition the flash drive beforehand. You shouldn't really need to make any special preparations. Make sure the flash drive doesn't contain any files you're going to want back again, make sure you copy those to some other disk.
You can partition the flash memory stick beforehand if you like, or you can use the Alternate Installation CD's partitioner to partition your drive. The Alternate Installation CD contains its own partitioner and it seems to be reliable. There's no reason not to use it except it displays the partition details in a list instead of showing you a graphical representation of your disks and partitions. A number of people seem to like partitioning beforehand with GParted so they can 'see what they're doing'. That's fine, it's okay to pre-partition a drive before installing. You don't have to but you can if you want.

> When I get to the part to install GRUB, I try to install it on the first   USB partition (i.e. /dev/sdb1) but the only partition it will install   on is /dev/sdb.In Gnu/Linux terminology, '/dev/sda', or '/dev/sdb', or '/dev/sdc' (without any number at the end), each refer to a different hard disk drive (or maybe a solid state drive or a flash memory disk or some other kind of disk drive). 
In the context of where you're going to install the GRUB boot loader, (or rather, the stage1 and core.img parts of GRUB), we're looking for a MBR.

In Gnu/Linux terminology, '/dev/sda1', or '/dev/sdb4', or '/dev/sdc3'  (where there is a number at the end), refer to specific partitions within a hard disk or  maybe a flash memory disk. 
In the context of where you're going to install the GRUB boot loader,  (or rather, the stage1 part of GRUB), these terms indicate the boot sector of a partition.
It's no longer a recommended practice to install GRUB's stage1 to a partition's boot sector. You should try installing GRUB to a MBR instead. 
A MBR has empty sectors after it for the core.img but a boot sector doesn't.

When installing Ubuntu in an internal disk of some kind (be it hard disk or SSD), when the disk is intended to remain inside the computer case, (fixed by screws usually), it normally best to install GRUB to /dev/sda, which means the MBR of the first hard disk.
If the device Ubuntu is being installed in is a removable disk then it's normally best to install GRUB to MBR in the removable disk. If your flash memory stick is /dev/sdb you should probably install GRUB to /dev/sdb unless there's some problem you haven't mentioned. Then the first stage of GRUB will go into the MBR and GRUB's core.img will be embedded in the next 46 or 48 or so sectors after the MBR. 
GRUB's files will still be installed in your /boot partition, which will be /dev/sdb1 if that's the one you told the installer to use for /boot. :)

---

### Post by cashmank on 2012-03-04
Thanks Herman. I had been having some problems when I initially installed GRUB to the MBR, but now it seems to be working better, depending on the machine I'm using.

---

