---
title: "Cannot Install Ubuntu 18.04.2 LTS"
date: 2019-05-03
forum: Installation &amp; Upgrades
---

### Post by ravenp1113 on 2019-05-03
When I try to install Ubuntu 18.04.2LTS from scratch using a USB, it will get to the installation screen then say, "Cannot create filesystem for ext4." It says it for ext3, ext2, you name it, It even says it for drive sda. I have had this problem for the past few months. I have been using Ubuntu from a live USB, with no hope. It says my system storage for the live USB is 2.0GB. I have spent hours trying to resolve the issue, with no fix, and it is very frustrating when the pc freezes, and I have to restart it, resetting everything. There is no other OS on my hard drive, I am trying to install this from scratch, straight onto the hard drive.

It also states about formatting the disks, which is totally fine, because I do not have anything on my drives.

When it fails, it just freezes the installation.

Thank you in advance,
                                  RP1806

---

### Post by oldfred on 2019-05-03
Is sda a working drive? 
What does Disks (gnome-disks) and icon in upper right corner Smart Status say about drive?

Was drive ever RAID?
Is UEFI/BIOS set to use drives in AHCI mode, not RAID nor Intel SRT?

Do you have current partitions?
sudo parted -l
sudo fdisk -lu

---

### Post by ravenp1113 on 2019-05-03
I created a partition of 300GB for ubuntu installation, when I boot my pc, it says the Hard disk will fail soon. It started saying that like 3-4 months ago, out of nowhere. One day it was fine, now it says that every time I boot the PC. I believe what caused it is when I had Windows 10, I tried to do a disk defragment, and my pc died during it, because it took hours. It shut off and would not turn back on to Windows. 

I believe the EUFI/BIOS is set to AHCI, and I cannot enter Gparted, it just stays on a never ending loop of, "scanning all disks" Thats it.

---

### Post by ravenp1113 on 2019-05-03
Ubuntu automatically put the drive back to default 500GB storage on disk, but the problem still persists.

---

### Post by oldfred on 2019-05-03
If drive has failed then best to not use it.
Did you get any info from Disks, it also can run checks, but all I know is that it reports drive is good or bad.

---

### Post by ravenp1113 on 2019-05-03
I have done a S.M.A.R.T test on it and usually the DNS passes, but all else fails. Thinking of just getting a new PC.

---

### Post by CatKiller on 2019-05-03
> **ravenp1113 said:**
> I created a partition of 300GB for ubuntu installation, when I boot my pc, it says the Hard disk will fail soon. It started saying that like 3-4 months ago, out of nowhere. One day it was fine, now it says that every time I boot the PC. I believe what caused it is when I had Windows 10, I tried to do a disk defragment, and my pc died during it, because it took hours. It shut off and would not turn back on to Windows. 

I believe the EUFI/BIOS is set to AHCI, and I cannot enter Gparted, it just stays on a never ending loop of, "scanning all disks" Thats it.

> **ravenp1113 said:**
> I have done a S.M.A.R.T test on it and usually the DNS passes, but all else fails. Thinking of just getting a new PC.

That disk is knackered. Get a different one. No need to get a different computer.

---

### Post by ravenp1113 on 2019-05-04
Ok, thanks

---

