---
title: "GRUB won't install on Lenovo Y580"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by SportsGuy2 on 2012-08-27
I recently purchased a Lenovo Y580 laptop. It has a 32GB SSD mSATA drive and a 1TB HDD. I tried to use the SSD for only Windows, but that wasn't working out (it was too small). I had to revert to Lenovo's "RapidDrive" where it uses both the SSD and HDD as the C:/ drive. 

I shrunk this volume for my Ubuntu installation and everything went smoothly except it wouldn't allow GRUB to install. It alerted me it wouldn't work on the partiton I chose and none of the other partitions would allow it to be installed on it, either. 

Any help is much appreciated! :D

---

### Post by oldfred on 2012-08-27
Is this like Intel's  Smart Response but on Lenovo?

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

That is seen as RAID and causes issues. But if you do not care about the use with Windows you can remove the RAID and use as a boot drive for Ubuntu.

You may have to remove Raid parameters on any drive that was RAID.

---

### Post by SportsGuy2 on 2012-08-27
When I put in "dmraid -ay", it says I have no raid disks.

I need to keep the Windows installation, but I have all of the repair disks I need.

---

### Post by oldfred on 2012-08-27
This may let the Desktop or liveCD see the RAID partitions so you can install grub correctly.

# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm

or Boot-Repair which automatically downloads mdadm

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

