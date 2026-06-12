---
title: "How to recognize disks more than 2TB during installation?"
date: 2012-01-02
forum: Installation &amp; Upgrades
---

### Post by iceinsouth on 2012-01-02
Hi, I have 4 hard drives that are 2TB each and I configured them as RAID10 so that they appear as one logic disk which should be 4TB. But when I loaded the Ubuntu installation ISO, it could only see a disk of 2TB. I am wondering if there is a solution to this. Thanks!

---

### Post by fdrake on 2012-01-03
this should do for you [http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)

---

### Post by darkod on 2012-01-03
The link above is for software raid, not fakeraid. You can use software raid if you plan to use only ubuntu. But in that case you need to go into the fakeraid you created, delete that array, and set the SATA mode in BIOS as AHCI, not RAID. In software raid ubuntu is creating the raid so you don't set it to RAID in the BIOS.

If planning to dual boot with windows you have to use fakeraid because it can't work on linux software raid.

But in any case, for RAID installs you need to use the Alternate Install CD (image), not the standard desktop. The alternate comes with raid support.

---

### Post by iceinsouth on 2012-01-03
> **darkod said:**
> The link above is for software raid, not fakeraid. You can use software raid if you plan to use only ubuntu. But in that case you need to go into the fakeraid you created, delete that array, and set the SATA mode in BIOS as AHCI, not RAID. In software raid ubuntu is creating the raid so you don't set it to RAID in the BIOS.

If planning to dual boot with windows you have to use fakeraid because it can't work on linux software raid.

But in any case, for RAID installs you need to use the Alternate Install CD (image), not the standard desktop. The alternate comes with raid support.

So the Alternate Install CD is text-based? What if I need to install GUI too?

Is it possible that I partition the disks first using live cd first? It seems that the default partition tool in the installation CD is cfdisk which cannot handle partition larger than 2TB.

---

### Post by darkod on 2012-01-03
Yes, the installer is text based but only the installer. At the end the desktop system is the same as if you installed from the desktop cd, you have same GUI etc. Exactly the same. Only the installer is text based and it has raid and lvm support.

I have rarely used it, and I partitioned during the install. But I never needed partitions/disks larger than 2TB.

Yes, you can boot the desktop cd in live mode, open Gparted and create partitions. I believe it can recognize the fakeraid array.
Then you should be able to use the alternate cd, it will ask you if you want to activate the detected raid, you say Yes and it should show the array.
Select which mount point goes to what partition and that should be it.

In theory, you can use the desktop cd too but there are additional steps to make sure grub2 is installed. More info here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

NOTE: I still prefer the alternate cd, it comes with native raid support and is recommended for raid. Other options might work, but you need to fiddle more.

---

