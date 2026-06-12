---
title: "raid1 for home partition"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by retaliator666 on 2012-11-26
I have 3 drives.
2x 1TB (this should become a RAID1 array)
1x 60GB solid state.

I want this configuration
/home mounted on the raid1
/, /tmp/ (encrypted), /var and swap on the 60GB solid state.

I find a lot of tutorials on how to install ubuntu (12.04) using the alternate cd. However, these tutorials only discuss installing the entire system on a raid, not just the /home partition.

Any tips (this is for ubuntu 12.04)?

---

### Post by darkod on 2012-11-26
It's the same. After you create the raid1 md device and it shows in your partitioning section, select it, choose the Use As as ext4 for example if that's the filesystem you want to use, and for mount point select /home instead of /.

Creating the md device is always the same. By selecting the mount point you choose how to use the md device.

For the partitions you will create on the SSD you will select the appropriate mount points and that's it.

---

### Post by retaliator666 on 2012-11-26
Thanks for your help Darko, I will try it out asap.

---

