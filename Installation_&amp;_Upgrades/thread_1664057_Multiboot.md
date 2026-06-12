---
title: "Multiboot"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by swisschris104 on 2011-01-10
I have the Zotac MAGHD, and when i got it I booted it with only Ubuntu 10.10 Meerkat. Now that I decided to buy some games, I cant get Playonlinux to work, and I was wondering how i can DUALboot my ubuntu, and windows 7 from only having Ubuntu on there, I got the windows cs tho

---

### Post by oldfred on 2011-01-10
Yes you can, but it somewhat depends on how you are partitioned. Windows requires a primary sda1 thru sda4 partition formated NTFS  with the boot flag. If dual booting with windows, you may want another NTFS partition for data. I do not recommend writing into the windows partition, but only read from it, to avoid the possibility of damage.

You also need a good liveCD or USB flash Ubuntu to reinstall grub. Windows will automatically install its boot loader to the MBR. After reinstalling grub to the MBR then you can run sudo update-grub so it finds windows.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

These are older discussing Vista but give some idea. You will want to reinstall grub2, so ignore any other info on grub legacy or other boot loaders.
Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

---

### Post by swisschris104 on 2011-01-31
> **oldfred said:**
> Yes you can, but it somewhat depends on how you are partitioned. Windows requires a primary sda1 thru sda4 partition formated NTFS with the boot flag. If dual booting with windows, you may want another NTFS partition for data. I do not recommend writing into the windows partition, but only read from it, to avoid the possibility of damage.
 
You also need a good liveCD or USB flash Ubuntu to reinstall grub. Windows will automatically install its boot loader to the MBR. After reinstalling grub to the MBR then you can run sudo update-grub so it finds windows.
 
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
These are older discussing Vista but give some idea. You will want to reinstall grub2, so ignore any other info on grub legacy or other boot loaders.
Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

so pretty much i just have to simply create 2 serpete apartiotions for windows, then Just use my live disk, and install grub? or just update it?

---

### Post by oldfred on 2011-02-01
Yes you can use gparted to create the NTFS partition from a liveCD. You cannot edit from any mounted partitions. You also may have to right click on the swap partition and swapoff to unmount it as liveCDs usually auto mount it to speed things up.

At least one NTFS partition has to be primary with the boot flag. Windows does not install to a logical unless it is a second install as windows only boots from a primary partition with a boot flag. Windows will read data from a logical partition.

Windows will install its boot loader to the MBR, so you have to reinstall grub2. See links posted before.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

