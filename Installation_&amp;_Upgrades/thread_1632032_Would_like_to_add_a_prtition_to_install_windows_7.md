---
title: "Would like to add a prtition to install windows 7"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by ganewbie on 2010-11-27
I wish to add a Windows 7 operating system to my computer maintaining my current operating system(s) (Ubuntu). I do not intend to replace my current internal hard drive or add a new one. My plan to maintain my internal hard drive. 
Here is my system's detail.

Please go in detail as I am a beginner.

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078fb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      181367  1456828416   83  Linux
/dev/sda2          181368      182402     8307713    5  Extended
/dev/sda5          181368      182402     8307712   82  Linux swap / Solaris

---

### Post by oldfred on 2010-11-27
Use gparted to shrink the linux partition and create a NTFS parititon. It must be a primary, but you can create sda3 as a primary. Move boot flag while in gparted to the new partition.

After installing windows you will have to reinstall grub2 to the MBR and after booting Ubuntu run sudo update-grub to get it to find the new windows install.

When dual booting I like to have a shared NTFS partition just for data. That way you do not have to write into the windows system partition, it is ok to read from it.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
chroot version:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by gordintoronto on 2010-11-27
Have a look at this:
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

Then search Google for "installing Windows 7 after installing Linux" and also do the same search with "Ubuntu" instead of "Linux".

---

### Post by ganewbie on 2010-12-01
Excellent information, however I was more cautions than I need.

1- Gparted was a amazing nice piece of software. Created the NTFS partition.
2- Installed Windows 7. Did all the updates and got running perfectly.
3- I was not comfortable with touching the GRUB and it was worth when I could not find the file menu.lst; but :
    a- I booted fromt he UBUNTU 10.10 DVD.
    b- Mounted the partition that has the Linux installed on.
    c- Install Grub as per the above tutorials or links.
    d- Restart to go back to Ubuntu and loos windows.
    e- run a simple GRUB update from a terminal and "voila" everything works like magic. and I can boot in either operating system with no issues what so ever.

Thanks for everybody's help, it was a fun adventure at the end. ;-)

---

