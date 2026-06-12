---
title: "Dual boot XP and Ubuntu Question Regarding Drives and Partitions"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by johnherrell on 2010-02-02
I am getting ready to install Ubuntu onto a desktop and have a couple of quick questions.

The machine is a Dell Optiplex GX280 MT 3.4GHz with 1.5GB of RAM and a 80GB hard drive.  The 80 GB hard drive currently has XP-Pro loaded onto it.

I plan on installing a secondary internal 500GB drive and using 250GB with the XP install and leave the remainder of the drive unpartitioned for Ubuntu.

BTW, I do plan on upgrading the Optiplex firmware prior to the Ubuntu OS install, as I have read there can be issues with the graphics if you do not.

Are there any issues installing this way?  Will the 9.10 installation handle installing Ubuntu onto this 2nd drive, MBR on the first obviously?  Or are there alternate ways to go about this?

Let me know your thoughts.

John

---

### Post by johnherrell on 2010-02-03
Anyone?  Planning on setting everything up on Thursday, just want to make sure there are no real surprises

---

### Post by darkod on 2010-02-03
I don't know anything about the specific Optiplex model, but as far as installing with multiple drives is concerned, you make the choices. Depending how you want everything set up, you can tell ubuntu where to install, and where to put grub2 (by clicking on the Advanced button on the last install screen, before clicking Install).

You should also be aware that when grub2 is on one disk MBR, and ubuntu on another disk, there might be delay in some cases. Unless it's impossible for you to boot from the disk where you want ubuntu installed, it's better to put grub2 on the same disk too. Then just set that disk as first in hdd boot order in BIOS.

---

### Post by oldfred on 2010-02-03
I prefer to have each operating system on a separate drive. Is the older 80GB drive getting so old you do not want to keep using it? You can still add an NTFS partition for data on the new drive and share data between Ubuntu & windows. I do that so my firefox and thunderbird profiles can be easily shared and I have the same data in both. It made my conversion to Ubuntu a lot easier (spouse did not see much difference). As Darko said it is better to have grub2 booting from the same drive as it is installed to. You could keep the windows boot on the 80GB drive and grub will find it and let you boot. I have seen windows users recommend separate data partitions even when running just windows. Since you have lots of new space plan on a separate /home and/or separate /data for Ubuntu. Then the root partition only has to be 10-20GB since data is elsewhere. Do you have any other plans for the new space, that can also change how you may want to set up new system.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Ubuntu data partition:
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

---

### Post by johnherrell on 2010-02-04
> **oldfred said:**
> I prefer to have each operating system on a separate drive. Is the older 80GB drive getting so old you do not want to keep using it? You can still add an NTFS partition for data on the new drive and share data between Ubuntu & windows. I do that so my firefox and thunderbird profiles can be easily shared and I have the same data in both. It made my conversion to Ubuntu a lot easier (spouse did not see much difference). As Darko said it is better to have grub2 booting from the same drive as it is installed to. You could keep the windows boot on the 80GB drive and grub will find it and let you boot. I have seen windows users recommend separate data partitions even when running just windows. Since you have lots of new space plan on a separate /home and/or separate /data for Ubuntu. Then the root partition only has to be 10-20GB since data is elsewhere. Do you have any other plans for the new space, that can also change how you may want to set up new system.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Ubuntu data partition:
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

Thanks for the info darkod and oldfred.  

I am indeed keeping the 80GB hardrive and leaving this as my XP PRO install.  I have a small number of server and database applications that I need to keep on that drive for testing purposes.  The new drive will offer me additional space, along with the ability for me to get back into other types of development.  

I am planning on installing MySQL and JBoss or Apache for some local development.  I am planning on creating 6GB swap partition, along with a home and data partition

---

