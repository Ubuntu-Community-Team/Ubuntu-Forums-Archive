---
title: "Dual boot for Ubuntu and Windows 8.1"
date: 2015-01-30
forum: Installation &amp; Upgrades
---

### Post by cr-theecho on 2015-01-30
Hi there,

I am receiving tomorrow this laptop: Acer Aspire V Nitro Black Edition VN7-791G-70TB.

storage: 256 GB SDD +  1 TB HDD.
memory: 16GB

It will come with Windows 8.1 pre-installed (I am not sure where, but I suppose on SSD).

The usage will be 95% Ubuntu with some several Windows machines inside and I will also need a native Windows machine for some games (as the video card will not work full speed in a virtual machine).

How do you recommend to partitions the drives (SSD + HDD)?

Thanks,
Cristi

---

### Post by oldfred on 2015-01-30
I would keep / (root) including /home on the SSD. But have no data (just user settings) in /home and use a /mnt/data partition on the hard drive for your data. Then you can link your data back to /home.
With my old XP I used two data partitions, one NTFS for any data I thought I might want when booted in either system, like Thunderbird email & Firefox profile. And then a Linux partition for the rest of the data. I also add a /mnt/backup partition on hard drive for some of the data on SSD and a smallish /mnt/backupSSD on SSD for the very most critical data on hard drive. Then I still backup to flash drives, DVDs etc.

       [URL="http://askubuntu.com/questions/461394/how-to-partition-ssdhdd"]http://askubuntu.com/questions/461394/how-to-partition-ssdhdd

[/URL]
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

[URL="http://askubuntu.com/questions/461394/how-to-partition-ssdhdd"]
[/URL]

---

### Post by cr-theecho on 2015-01-30
Thanks for the answer (and the link), will take a look when I have the laptop.

Cheers,
Cristi

---

### Post by cr-theecho on 2015-01-31
I have the laptop now, windows is installed on SSD, I shrinked that SSD partition and left like 150GB for Ubuntu. I will install ubuntu / and /home on the SSD but how can I mount data of home to point to the HDD?

---

### Post by oldfred on 2015-01-31
You need to use Something Else when you install.
First link in splitting /home, post #4 also has details.

Be sure to fully backup Windows and the efi partition before installing Ubuntu.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Then after the install use gparted to create the data partition. I prefer to mount at /mnt/data and use links as shown in the posts above. Others mount at /media/$USER/data. You want to create a permanent mount in fstab and give yourself ownership & permissions to use it.


 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

      
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Specific commands to copy template into fstab and mount either NTFS or ext4 partition.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

