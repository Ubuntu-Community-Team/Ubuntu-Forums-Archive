---
title: "installing dual boot on raid1: ubuntu and windows disagree about partition size"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by Zed on 2008-07-08
My new work machine came with 2 150GB drives configured for RAID1 in the BIOS (of an ASUS P5B deluxe mobo.) They were subsequently divided into 65GB and 85GB partitions. I followed the [Fakeraidhowto](https://help.ubuntu.com/community/FakeRaidHowto) and its pointer to directions to [resize your Windows partition](http://gentoo-wiki.com/HARDWARE_Dell_Precision_690#Repartition_RAID0_Storage_Array). My intent was to resize the 85GB partition to 10GB. I finished the 'repartition storage array' step, doing both an ntfsresize and an fdisk, and booted into Windows. Windows didn't run a chkdsk, so I did it by hand.

Now Windows still says the second partition is 85GB, but if I boot back to into the LiveCD, it tells me it's 10GB. 

My problem probably lies in that those directions were for RAID0 and I've got RAID1. Can anyone please tell me what state I've gotten my system into, and how to get from there to where I want to be (with the second partition split into 10GB and 75GB partitions, and without having broken my Windows installation.) Thanks.

---

