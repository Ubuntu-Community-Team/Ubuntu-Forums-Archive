---
title: "Create a disk image of ubuntu and convert boot to pxe compatible server"
date: 2022-05-04
forum: Installation &amp; Upgrades
---

### Post by drc0rt3x on 2022-05-04
Hi to all, in my pc I have both Oracle Virtualbox that Vmware Workstation with an instance of a virtual machine with ubuntu 22.04 (installed) as guest and windows 10 as host. Since I want use the network boot feature (PXE) from my pc I want know if it's possible make an image of Ubuntu guest system in ntfs format from a boot utility (such as Acronis True Image) because the pxe server will be a windows xp pc (so the ISO image can't contain ext format)... It's possible copy and past the content of entire virtual hard drive?

Moreover I want know what and how modify the boot files of the image to make operating system guest compatible with pxe server. So, in little words, I want know how transform a virtual machine to a pxe system.

Note: Option to exctract iso files of ubuntu iso image and run livecd is not accomplished because I don't have empty drive and don't want create partition on the existing drives to install a new istance of ubuntu.


Note2: the windows 10 system (that actually is the host system) will act as if is diskless, so at boot I will enter in the bios, select as boot the network boot and the ssd drive build in will remain untouched (in other words I don't have the need to install the same ubuntu image to more than 1 pc in the network).

Note3: it's possible make network boot with the permission to write to server? I have read that network boot is read-only type


Hope that somebody will help me


Thank You

---

### Post by drc0rt3x on 2022-05-12
nobody?

---

### Post by yancek on 2022-05-12
The link below discusses cloning a virtual machine using vmware.

[https://www.liquidweb.com/kb/vmware-cloning/](https://www.liquidweb.com/kb/vmware-cloning/)

I have no idea how it will work, I've never used VMWARE.  Never used Acronis nordone a PXE install so can't help with that either.

You can't run Ubuntu or any Linux OS from an ntfs partition but if it an ISO format the filesystem on which you have the iso file does not matter as the iso will be iso9660 format.

---

