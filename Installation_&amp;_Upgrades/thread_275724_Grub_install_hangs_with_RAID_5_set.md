---
title: "Grub install hangs with RAID 5 set"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by Akhran on 2006-10-11
I have configured a simple RAID 5 disk set of the following configuration during the installation:

RAID5 Device #0 
#1 20GB f ext3 /

SCSII (0,0,0) sda
#1 primary 256.0 MB F swap
#2 primary 10 GB K RAID

SCSII (0,1,0) sdb
#1 primary 256.0 MB F swap
#2 primary 10 GB K RAID

SCSII (0,2,0) sdc 
#1 primary 256.0 MB F swap
#2 primary 10 GB K RAID

When installing the GRUB on the MBR, "Running grub-install (hd0)" hangs at 50%.

Please advise.

Thanks!

---

### Post by reison on 2006-12-31
I've got pretty much the same problem and can't seem to find any answers. Have any luck getting it to work?

---

