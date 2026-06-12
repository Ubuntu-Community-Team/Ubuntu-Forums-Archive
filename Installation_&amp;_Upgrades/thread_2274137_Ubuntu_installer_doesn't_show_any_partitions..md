---
title: "Ubuntu installer doesn't show any partitions."
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by Kakaji on 2015-04-18
Hi! I'm new to Ubuntu. I have a Dell Inspiron laptop with Windows 8.1 pre-installed, it is a UEFI computer. I want to install Ubuntu 14.04 alongside windows using live USB.
I turned off fastboot, secure boot, shrunk the partition and tried to install ubuntu as one would but after I connect to the wifi during the installation, the menu where "Something else" and other options should be doesn't appear at all. Instead I'm directly taken to the next menu where I'm supposed to select the partition on which to install Ubuntu. But the problem is that menu doesn't show any partitions, it's totally blank. GParted does detect my hard disk. What should I do? Please help. Thanks in advance.

---

### Post by oldfred on 2015-04-19
I just installed to a Dell small desktop.
But I used Windows to shrink the NTFS partition, rebooted to allow it to run chkdsk & update to new size. 
Then I used gparted to create the partitions I wanted including / & /mnt/data. But I only used / during install. Formatting with gparted becomes optional as you reformat again using Somethign Else install option. It should show partition and you click on it, then the change buttom.

My system was a newer Haswell system, so I installed 15.04 even though not yet released. My main desktop uses 14.04 as it is a Long Term Support version.

Did you turn off a fast boot in UEFI. That is different than the fast startup or always on hibernation in Windows. I had lots of fun?, finding that setting & getting it changed in Windows.
And I took a couple of days to do all the backups of Windows with Macrium, Windows recovery (repair disk), and Dell recovery as I had to go buy another flash drive. 
Each backup took a couple of hours, but my Ubuntu install after pre-partitioning took 10 min with relatively high-speed Internet.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
      
 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

Also see links in my signature.

---

