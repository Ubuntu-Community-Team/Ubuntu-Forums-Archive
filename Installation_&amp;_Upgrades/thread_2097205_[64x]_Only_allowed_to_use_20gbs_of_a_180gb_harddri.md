---
title: "[64x] Only allowed to use 20gbs of a 180gb harddrive"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by MarcDavies on 2012-12-22
Hi i have a problem when installing my Ubuntu onto a brand new harddrive. I am dual booting my computer with windows 7 from one harddrive and ubuntu on the other.

When it is installed and all set up on the new harddrive the system only allows me to use 20gb/s of my hard drive for storage of file an folders and other programs. I am a Computer science Student who does alot of programming and i need all the space on my harddrive but I cant see to extend the limit Ubuntu has placed.

I am using a 180gb hard drive and i used the Windows7 wubi installer to install ubuntu onto the harddrive.

any help would be greatly appreciated thanks.

---

### Post by oldfred on 2012-12-22
Welcome to the forums.

Wubi is an extended test for Windows users. It is limited in size and is just a file on a Windows NTFS partition. It uses the Windows boot loader and is not a true dual boot. But avoids the issues of new partitions which new users are not familiar with.

If you want to install to a second drive you should just do a full partitioned install. Many suggest physically disconnecting Windows drive so all of Ubuntu is on second drive. If you use Something else or manual partitioning and on partition screen choose to install grub2's boot loader to the drive that is the second drive (usually sdb) then you do not have to disconnect drive.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

    
       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

