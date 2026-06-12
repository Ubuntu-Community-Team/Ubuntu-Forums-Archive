---
title: "Need help to test that my disk copy succeeded"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by whodidntante on 2008-06-01
Hi,

I am using a Gateway desktop PC with an Intel 975x chipset, and I would like to make Linux my primary OS.  However, I must retain Windows and the Gateway recovery partition.  The PC has three SATA disks.

1) 250 GB 
2) 250 GB
3) 750 GB

Disks 1 and 2 are member disks in a RAID 0 array (Intel Matrix), and disk 3 is a normal disk.  I used SelfImage to disk copy the RAID 0 array to disk 3, and I intend to break the RAID 0 array and use those disks for Linux.  However, I need to test that my copy to disk 3 works first, Windows and recovery partition, without risking my data.  I backed up important data an external drive, but it takes at least a week to install Windows and get it to a point where it works the way I want, so I want to avoid that.  

I tried booting to Disk 3 using the boot menu, a feature of the BIOS, and it boots fine, but I don't know how much it is really accessing from disk 3, and how much comes from the RAID array (since this is still C).  

How can I safely test that my disk copy is good, before breaking the array?

---

### Post by Lord Landis on 2008-06-01
Physically remove the RAID drives and see if it still boots.  If it does, then you're good.  If not, re-connect the drives.  Since you've made no changes to the controller or the logical volume, it should come right back up.

Also, try changing the boot device order in your BIOS to put the non-RAID volume first in line.

---

### Post by whodidntante on 2008-06-08
That's what I thought about doing, but I couldn't find any documentation that says this would not be destructive.  

Can anyone familiar with this chipset confirm that doing this is safe?

---

