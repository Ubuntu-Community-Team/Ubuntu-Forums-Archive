---
title: "/dev/sdc and GRUB install woes"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by oblio9 on 2007-06-08
I am trying to install Ubuntu Studio and bought a separate hard drive for it. I have an EPOX mobo with the 590 SLi nvidia chipset. I have 2 sata drives on RAID 0. I added another sata drive (320 GB). I want the new drive to have ~200 GB for linux and ~120 GB as a FAT32 partition for holding mp3's and photos. I have tried installing U-Studio multiple times, in various ways and can't get GRUB installed correctly. 

The 2 RAIDed drives (sda and sdb) have widnows installed. I want GRUB installed on the MBR of /dev/sdc. When I go through the default installer it installs GRUB on hd0 which appears to correspond to sda whcih blows away the MBR for windows which I then have to go in and fix (no big deal). If I then reboot and go into system rescue mode I can install GRUB to /dev/sdc  (as long as /dev/sdc1 is not bootable) but when I reboot it says it can not find the disk specified and if I go in to edit the options it looks like it is trying to boot to (hd0,0)

Anyone run into this or have any thoughts? Appreciate any help at all. Thanks.

---

### Post by easygoing on 2007-06-08
Hi,
I have the exactly the same disaster on my Dell XPS 400. I did much worse as I have not yet recovered my WinXP.
Please see [http://ubuntuforums.org/showthread.php?t=468519](http://ubuntuforums.org/showthread.php?t=468519) for details.
I wonder if I can install 6.10 successfully in this situation, and access my files on WinXP.
Does any good thing has to go bad with time? Can our fellow software engineers working on Linux really improve the system rather than releasing half-baked buggy features again and again. I was disappointed to see Linux fell to this miserable state.

---

### Post by pt123 on 2007-06-09
Try these instructions replace the device names in accordance to your system. 

12. Inorder to change the grub used from the new linux installation
to the copied installation
Edit the menu.lst in the copied installation
find groot
and change it to point to this partion
so hda3 becomes -
groot (hd0,2)
13. Then run
update-grub
To refresh other menu entries with new grub device
14. Then run
grub-install /dev/hda

---

### Post by oblio9 on 2007-06-09
easygoing- It is a pain but it's also a somewhat unique setup and I don't expect linux to "just work" every time. I'm guessing if I did an expert install this could all be sorted out except I don't know what half of the options mean. I had this working fine when I had it on a PATA drive in the same system. I think it's the SATA setup that it's tripping over.

pt123 - I'm not really following. I can't really even get into a working environment.

Heck I'll even use a boot floppy if that makes this easier, I just want to get this working.

---

### Post by confused57 on 2007-06-09
> **oblio9 said:**
> easygoing- It is a pain but it's also a somewhat unique setup and I don't expect linux to "just work" every time. I'm guessing if I did an expert install this could all be sorted out except I don't know what half of the options mean. I had this working fine when I had it on a PATA drive in the same system. I think it's the SATA setup that it's tripping over.

pt123 - I'm not really following. I can't really even get into a working environment.

Heck I'll even use a boot floppy if that makes this easier, I just want to get this working.
If you had it working with a PATA drive, there could possibly be a problem with installing grub to the SATA mbr.

You could try reinstalling grub to the Ubuntu drive's mbr with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
root (hdx,y)
setup (hdx)

see if this gives  you a grub menu when you boot first to the Ubuntu drive, if you do, highlight your Ubuntu entry, press "e", change root from (hdx,y) to (hd0,y), then press "b" to boot.

If this doesn't work, then you could try installing grub to the root partition, also using the live cd, see the link, but it would be:
root (hdx,y)
setup (hdx,y)

then you might be able to make a GAG floppy to boot the Ubuntu partition:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

An even better idea might be to burn a copy of the Super Grub Disk(5-7 Mb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
grub doesn't need to be installed to the root partition to boot Ubuntu with SGD

I'm not sure any of this will work, but might give you some ideas to try.

---

### Post by pt123 on 2007-06-09
> **oblio9 said:**
> 

pt123 - I'm not really following. I can't really even get into a working environment.




Have you tried using the Live CD?

---

### Post by easygoing on 2007-06-10
What I found out is that Dell WinXP Recovery CD is amazingly good. Although I wasted some time in trying recovery mode without success, I went straight to install a new copy of WinXP in the existing partition. After 1 hour, I have everything back in perfect working order, along with all my settings and installed software. Even the latest games work right away.
Of cause, dot Net framework gave several warnings. The cause is that WinXP registry has reference to .Net Framework 1.1 functions, but the Recovery CD only installed .Net Framework 1.0. I researched this problem online and solved it easily by upgrading to .Net Framework 3.0.
Since I have some coding projects in mind and some software and framework only work under Linux, I do not feel the desire to spend too much time on the Linux OS itself. So I re-installed CentOS 5, and tolerate the problem of startx every time I log in. Now at least I can work and play.
As for GRUB installation directory, CentOS has one screen dedicated to this task. The default is the device that / is on. That is why I did not have trouble. Linux only sees 3 devices sda, sdb, sdc, and my decision to set / on sdc1. So I think the problem of Kubuntu is that the developers did not expect people to use hardware boot managers to select which device to boot from, and was lazy to show the GRUB installation device in a consistence way as the partitions. I felt that this is a broken feature.

---

