---
title: "VMware AND Disk Partition"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by j3nn1 on 2008-03-27
**This post could be related to an Ubuntu bug filed at**: Hi!

I would like to thank everyone from this forum that has been helping speed-up my learning process of Linux. After many trials with Fedora 8, I decided to use Ubuntu 6.06. I have a school project and this project involving running two instateenous of Windows Server 2003 on VMware Server version 1.5 with Ubuntu as host OS. The following are output from invoking fdisk -l command:
Device Boot Start End Blocks Id System
/dev/sda1 1 1305 10482381 83 Linux
/dev/sda2 1306 1828 4200997+ 83 Linux
/dev/sda3 1829 3916 16771860 83 Linux
/dev/sda4 3917 7296 27149850 5 Extended
/dev/sda5 3917 4700 6297448+ 83 Linux
/dev/sda6 4701 5222 4192933+ 82 Linux swap / Solaris
/dev/sda7 5223 7296 16659373+ 83 Linux


and output from invoking cat/etc/fstab:
# /etc/fstab: static file system information.
#
# &lt;file system&gt; &lt;mount point&gt; &lt;type&gt; &lt;options&gt; &lt;dump&gt; &lt;pass&gt;
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda3 /Server2003-1 ext3 defaults 0 2
/dev/sda7 /Server2003-2 ext3 defaults 0 2
/dev/sda2 /boot ext3 defaults 0 2
/dev/sda5 /home ext3 defaults 0 2
/dev/sda6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

If I need to change file system type on /dev/sda3 from ext3 to ntfs, what is (are) the command(s) that need to be invoked? umount -t ext3 /dev/sda3; mkfs -t ntfs /dev/sda3, mount -t ext3 /dev/sda3. I am using WMWare Server ver.1.5 and installation of Server2003 by &quot;creating a new virtual disk option&quot; only allows OS to be created at /dev/sda1 (the disk volume is very limited and might not enough for Active Directory and Server2003). At the same time, installation by using &quot;physical disk&quot; option at /dev/sda3 does not allow Server2003 to be installed on /dev/sda3 because file system, in this case ext3, is not recognized the file system (I expected this). Am I going to the correct direction for this issue, such as installing the correct application such as VMware Server? If everything doing weel, I also would like to change file sy [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi!

I am in the process of learning Linux and have decided to use Ubuntu 6.06. I have a school project and this project involving running two instantaneous of Windows Server 2003 on VMware Server version 1.5 with Ubuntu as host OS. The following are output from invoking fdisk -l command:
Device Boot Start End Blocks Id System
/dev/sda1 1 1305 10482381 83 Linux
/dev/sda2 1306 1828 4200997+ 83 Linux
/dev/sda3 1829 3916 16771860 83 Linux
/dev/sda4 3917 7296 27149850 5 Extended
/dev/sda5 3917 4700 6297448+ 83 Linux
/dev/sda6 4701 5222 4192933+ 82 Linux swap / Solaris
/dev/sda7 5223 7296 16659373+ 83 Linux


and output from invoking cat/etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda3 /Server2003-1 ext3 defaults 0 2
/dev/sda7 /Server2003-2 ext3 defaults 0 2
/dev/sda2 /boot ext3 defaults 0 2
/dev/sda5 /home ext3 defaults 0 2
/dev/sda6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

If I need to change file system type on /dev/sda3 from ext3 to ntfs, what is (are) the command(s) that need to be invoked? umount -t ext3 /dev/sda3; mkfs -t ntfs /dev/sda3, mount -t ext3 /dev/sda3. I am using WMWare Server ver.1.5 and installation of Server2003 by "creating a new virtual disk option" only allows OS to be created at /dev/sda1 (the disk volume is very limited and might not enough for Active Directory and Server2003). At the same time, installation by using "physical disk" option at /dev/sda3 does not allow Server2003 to be installed on /dev/sda3 because file system, in this case ext3, is not recognized the file system (I expected this). Am I going to the correct direction for this issue, such as installing the correct application such as VMware Server? If everything doing weel, I also would like to change file sytem at /dev/sda7 to mount the second Server2003. Thank you for your contribution!

---

