---
title: "RAID + LVM install on Kubuntu"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by durist on 2006-11-02
I'm trying to install Kubuntu Edgy on LVM+RAID. I can create the RAID arrays via the installer on the alternate CD, and I can create LVM volumes, but I can't find a "Configure LVM" option to configure LVM volumes with filesystems in the installer, as mentioned in the [LVMOnRaid]("https://help.ubuntu.com/community/Installation/LVMOnRaid") docs.
It seems to be impossible to install my root filesystem onto LVM.

I've also tried the installer from the Desktop CD, but that doesn't even offer RAID as an option. Am I missing something, or has this feature been cut, or is this a bug?

---

### Post by Walldorf2000 on 2006-11-21
It works with my Xubuntu 6.10 alternate install CD. After creating a Volume Group for the raid device I could add the logical volumes. I remember that I had to search some time :confused: Maybe the trick was to leave the partitioning and restart it :confused: 

While I managed to create and format all the volumes and the installation went through without any problems, I failed to boot the system. It hangs while doing fsck. (/boot is a separate partiton outside of LVM.)

I guess I have to spend my next weekend to check what's going wrong ](*,)

---

