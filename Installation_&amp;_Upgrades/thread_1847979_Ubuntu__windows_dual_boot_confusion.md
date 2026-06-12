---
title: "Ubuntu / windows dual boot confusion"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by samsanchez on 2011-09-21
Hi

I need to install Ubuntu Natty on an existing system with Windows Vista.

Here ([http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)) It says that you can just start the live CD and choose "Install Ubuntu alongside Windows".

But here ([http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/](http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/)) It says that you have to reduce the size of the windows partition from within windows, and then start up the Ubuntu live CD and manually specify the boot and swap partitions.

Which is true?

---

### Post by Hakunka-Matata on 2011-09-21
They're both sort of true.  It does depend on your disk storage space available though.  

What does your disk(s) look like now?

Windows Disk Management - gparted if you're in ubuntu

---

### Post by oldfred on 2011-09-22
Most of us still recommend using Windows to shrink the Windows NTFS partition. When Vista came out Windows changed from XP & LInux's standard sector start of sector 63 to sector 2048. Version of gparted that are that old may still move the start of Windows to sector 63 and then you have to do Windows repairs. All new versions of Gparted & the installer for the last year or so start all first partitions at sector 2048 and there is no issue.

But it still is a good ides to have a Windows repair CD and good backups all all important data whenever making system changes.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by samsanchez on 2011-09-22
> What does your disk(s) look like now?

I don't know. I'm helping a friend who needs access to Linux but wants to keep windows as well. I haven't seen their computer yet.

What's the rule concerning disk storage space?

---

### Post by Hakunka-Matata on 2011-09-22
> **samsanchez said:**
> I don't know. I'm helping a friend who needs access to Linux but wants to keep windows as well. I haven't seen their computer yet.

What's the rule concerning disk storage space?

Your next step would be to have a look at the HDD partitioning scheme on your friend's computer's disk.  You will need either:

[LIST]
[*]one free primary partition (MBR/BIOS HDD's have a maximum of 4 primary partitions) and 25GB unallocated space, **OR**
[*]an existing Extended partition with at least 25GB free (unallocated space) available.
[/LIST]
note: 25GB isn't a hard rule, but a practical limit.

---

### Post by samsanchez on 2011-09-23
Ok,so basically if they have 25mb free, then the automatic "install Ubuntu alongside Widnows" option should work fine, without repartitioning in Windows first?

---

### Post by Hakunka-Matata on 2011-09-23
> **samsanchez said:**
> Ok,so basically if they have 25mb free, then the automatic "install Ubuntu alongside Widnows" option should work fine, without repartitioning in Windows first?
No, that is not necessarily true.  Information on how the hard drive is currently partitioned is required before any specific suggestions can be made.
Boot the computer from an Ubuntu LiveCD/USB install disc, open a Terminal window and, 
please post the output of 
```
sudo sfdisk -lus && sudo fdisk -l
``` from your friends computer.

---

### Post by samsanchez on 2011-09-23
Here it is:

```
 unrecognized format - using sectors

Disk /dev/sdb: 19457 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        63 291454975  291454913   7  HPFS/NTFS
/dev/sdb2     291454976 312573951   21118976   7  HPFS/NTFS
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82df4bb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18143   145727456+   7  HPFS/NTFS
/dev/sdb2           18143       19457    10559488    7  HPFS/NTFS
 
  
```

---

### Post by oldfred on 2011-09-23
You have two available partitions in both drives. But I am always leary of any auto process that I do not know exactly what it is going to do. Some versions of Ubuntu did not clearly show the use entire partition meant use entire drive or erase Windows.

If you use manual install or something else in Natty you have to create partitions as ext4 & use as / (root) and swap no format. 

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

