---
title: "Installing ubuntu on laptop with SSD and HDD. Which partition should go on which driv"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by shaansweb on 2014-11-14
Hey everyone,

 I want to set up a windows/ubuntu dual boot on a laptop with a 32 GB SSD and a 500GB HDD. Does anyone know how I should partition this? I'm thinking / on the SSD, and /home, /boot, and swap on the HDD. Does this sound good? Should /var and /tmp be their own partitions? On my current install, they are just part of the / partition. What's the benefit of making them their own partitions as opposed to being part of / and should they be on the SSD or HDD?

Thanks in advance

---

### Post by yancek on 2014-11-14
Which windows version are you using?  It would be simpler to install just the / and maybe a separate /home partition on the larger drive.  Lots of new users have problems with a separate /boot partition as they get filled quickly resulting in an unbootable machine.  No reason to have separate partitions for /var unless you are using it as a server.  I'm not sure why you would want /boot on a separate hard drive from the / filesystem although there is no reason you could not do that.

---

### Post by shaansweb on 2014-11-14
I'm using windows 8.1. When setting up my current install, I couldn't get the dual-boot to work properly because of uefi/fast-boot/whatever-it's-called nonsense until I deleted the partitions and installed again using a /boot partition. From that experience, I assumed a /boot partition is necessary to dual boot with uefi. Is that not the case?

---

### Post by ajgreeny on 2014-11-14
No, there is no need for a /boot partition though one is added by default if you choose to use encryption or LVM for your install.

For the best advice on using UEFI have a good read through [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by yancek on 2014-11-14
If you have windows 8.1, particularly if it was pre-installed when you got the computer, it is probably booting in EFI mode.  If so, there is an EFI partition at the beginning of the drive which is formatted as FAt32 and if your windows 8 is installed EFI, then you must also install Ubuntu EFI and not install the Grub bootloader to the MBR.

---

### Post by oldfred on 2014-11-14
From the live installer's terminal post this to confirm your Windows is UEFI.

sudo parted -l

Because you have two drives you will need to use Something Else. 
       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Was SSD part of a Windows cache using Intel SRT? That is pretty much the same with all brands of systems. You do need to turn off SRT can change to AHCI. You may need to remove old RAID (which SRT uses) meta-data on drive.
      
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

