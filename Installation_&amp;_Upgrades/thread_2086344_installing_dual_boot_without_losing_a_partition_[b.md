---
title: "installing dual boot without losing a partition [beginner]"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by Knez13 on 2012-11-20
My Windows XP is getting a little old so I've decided to try out a dual-boot configuration with Ubuntu. I have 5 partitions on 3 drives as shown in the image:

[IMG]http://i1224.photobucket.com/albums/ee376/knezmilos13/Clipboard01-4.png[/IMG]


I was planning to delete partition F and then split it into two partitions (one goes for swap, right?) during installation using Linux file system. However, it seems that deleting F (primary) will also kill G (extended) partition which is full of my data. So my question is:

How do I install Ubuntu on F without killing G? I heard that it's possible to install Ubuntu on NTFS, but I also that it's not such a good solution.

Thanks in advance.

---

### Post by darkod on 2012-11-20
Deleting the primary partition does not delete the extended. You should be able to easily delete the 100GB partition in Disk Management, leave the space as unallocated, and then create the partitions you want during the ubuntu install. I always prefer the manual method (Something Else) if you are willing to create the partitions yourself. The manual install also allows you to select bootloader location, which is important with three disks because you need to put grub2 on the disk where you plan to boot from.

---

### Post by Knez13 on 2012-11-20
Thanks for your quick answer :)
So ... it's safe to delete then? It says "All data on this volume will be lost"?

About that other stuff, is there going to be a problem if Windows boots from C: and Ubuntu from F: since they are on separate disks? Where should I install grub then? I was told to set it automatically, is that alright for my configuration? I'll still be using Windows more and might reinstall/remove/replace Ubuntu, so should I then put grub on C: or F: ?

---

### Post by oldfred on 2012-11-20
Boot loader have to be in an MBR for BIOS to be able to use it to boot. Only if you have another boot loader to chain to another system might you install elsewhere. Windows will not easily chain load to Ubuntu.

So install grub2's boot loader to the drive you install Ubuntu and in BIOS select that drive to boot from. Grub will had a menu item to chain load to the Windows install and let you choose which system to use. If you uninstall Ubuntu you can change BIOS back to boot the Windows drive.

Any auto installs of Ubuntu will normally overwrite the Windows boot loader in sda. So best to use manual install or Something else to install.

You can have up to 4 primary partitions with MBR partitioning per drive. One primary can be an extended partition which is the container for many logical partitions.  If you use manual install you can create both / (root) in a primary and swap can then either be primary or logical. G: then remains as another primary. 

Pay attention to last .png as it shows the combo box on which drive's MBR to install grub2's boot loader.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

