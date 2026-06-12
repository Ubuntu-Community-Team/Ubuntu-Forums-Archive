---
title: "failed to crate raid 1 array"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by SkyHiRider on 2010-07-14
Installed Ubuntu server 10.04 on my machine with two disks. Installation goes fine. When I try to boot the system grub does not load immediately, takes a few seconds then boots the system. During startup it says my /home folder is broke, if I want to manually fix it. 

When I go to the console and check the raid array my home partition is syncing and the other raid partitions are broken. Fdisk -l says that some of the partitions end with a bad sector count or somethign like that. Refortmattig and reinstalling does not help, even tried different setups but it's getting really annoying trying ot do it the try one thing at a time way. 

Anyone had similar issues that they managed to fix?

---

### Post by YesWeCan on 2010-07-14
Have you seen this? [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

---

### Post by SkyHiRider on 2010-07-17
I did all that over and over. Debian managed to install the raid array fine using the XFS filesystem, thou I had some difficulties. But installing Ubuntu with ext4 is a no go, and I can do all the basic stuff.

Any way to format the whole drive or at least remove any and all MD device info from it. I have a hunch that It did not erase the MD settings and now the partitions are getting mixed up with the old non existent ones.

---

### Post by YesWeCan on 2010-07-17
When I used RAID1 with 10.04 I had trouble with dmraid messing things up during boot and had to uninstall it. I also had a problem with mdadm getting its drive letters mixed up when it scanned. I fixed this in the /etc/mdadm.conf file by telling it to scan the uuid of the RAID disks. I don't know whether your difficulties are related but I would definitely unistall dmraid if it is installed.

---

### Post by SkyHiRider on 2010-07-21
I "fixed" it by installing Debian again with XFS. Really wanted to try ext4 with raid 1, but it took too long with no viable results.

---

