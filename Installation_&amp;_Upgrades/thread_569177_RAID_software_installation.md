---
title: "RAID software installation"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by GoldEmish on 2007-10-06
Hello everybody,
i'm a linux noob and i'm tryng to install a simple FTP server with gnome, using 2 disk in raid1.
I found 2 ways:
- alternate CD install with "Configure RAID Software" options
- mdadm installation

With the first mode, i can not run Nvidia drivers. ServerX doen't start and installing Nvidia original package tells me that the kernel version is mismatch and so on...

With the second mode i perform a normal installation with the desktop live CD. Xserver doesn't work but, with this installation, Nvidia package works. Than rebooting everything well started. Now I need to built thehe RAID array with mdadm. But i can not understand if i can built an array from an system partition. I have two disks with the same partitions, but in the first is running the SO. If i try to built the array mdadm tells me that /dev/sda1 is locked (in use).... of course it is the system partition! But with mdadm can't I use just 2 disks? I must have 3 disk, 2 for the arrat and another for the SO?

Please helps me and sorry for my poor english :confused:

---

### Post by GoldEmish on 2007-10-07
:confused:

---

### Post by Slim Backwater on 2007-10-07
> **GoldEmish said:**
> Hello everybody,
i'm a linux noob and i'm tryng to install a simple FTP server with gnome, using 2 disk in raid1.
I found 2 ways:
- alternate CD install with "Configure RAID Software" options
- mdadm installation

With the first mode, i can not run Nvidia drivers. ServerX doen't start and installing Nvidia original package tells me that the kernel version is mismatch and so on...

With the second mode i perform a normal installation with the desktop live CD. Xserver doesn't work but, with this installation, Nvidia package works. Than rebooting everything well started. Now I need to built thehe RAID array with mdadm. But i can not understand if i can built an array from an system partition. I have two disks with the same partitions, but in the first is running the SO. If i try to built the array mdadm tells me that /dev/sda1 is locked (in use).... of course it is the system partition! But with mdadm can't I use just 2 disks? I must have 3 disk, 2 for the arrat and another for the SO?

Please helps me and sorry for my poor english :confused:

The Alternate CD is the way to go, I've done it, but had no X or video problems.  Complete the installation with the Alternate CD and then troubleshoot the X and nVidia problem separately.

Try running a sudo apt-get update and sudo apt-get upgrade before the nVidia package. (on the other hand, if that's what you are doing, then try the opposite, put in the nVidia package first)

Which nVidia package are you using?  If it's from the nVidia site, and you're doing the manually installation, then I *think* you need to install build-essential first, and possibly the kernel headers so that the nVidia package can build a kernel module.

You've probably seen these:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

but maybe they can offer some help.

Your second option is hard work; Trying to move a running system onto a new RAID-1 is hard and a lot of work but can be done.  Basically you create a degraded RAID-1 on the other drive, format and copy everything to it, manually install GRUB, boot off it, then add the original drive as a spare. I've done this too, but strongly recommend that you do this during installation.

Finally, give the 7.10 Beta a try.  It might work perfectly for you and later this month you can just update to the release version.

Good luck.

---

