---
title: "Single partition across two disks"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by swhite58 on 2012-02-12
I'd like to do a clean single boot install of Ubuntu onto two 1.5 Tb disks, with a single main partition across both disks. This is a home server, and performance isn't really an issue.  I will also be getting an external disk for backups.  What's the best way to do it?

I suspect I can use RAID somehow, but what about LVM?   

Can I set up the partition across both disks first then install, or would it be better to install onto one disk and extend the partition to the second afterwards?

Thanks

---

### Post by jerrrys on 2012-02-14
raid 0

[http://en.wikipedia.org/wiki/Raid_0#RAID_0](http://en.wikipedia.org/wiki/Raid_0#RAID_0)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=raid+0&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=raid+0&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2012-02-14
I do not know RAID nor LVM.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

But be sure to have good backup procedures as either if RAID or LVM fail all data is lost from both drives.

---

### Post by tamkt on 2012-02-14
This server, you used to do ?
If server hasn't hard raid, you should split partition for home directory.

Sorry bad english.

---

### Post by Lars Noodén on 2012-02-14
You can do this with RAID 0.  I recently set up a Debian system with one RAID 0 disk, which is quite similar to Ubuntu.  With Ubuntu, I think you might have to use the Alternate installation DVD (used to be CD).  

When you get to the disk partitioning, it is just a matter of choosing two or more physical volumes for RAID.  Then after the rest of the space is partitioned, choose Configure Software RAID, select the array components, and then the RAID array gets built.  Then you can format the newly made RAID device.

---

### Post by darkod on 2012-02-14
Actually I would rather go with LVM, and not RAID0. Reasons:
1. With RAID0 you still need to create partitions with fixed size. Yes, you can resize later but it's a hassle. With LVM you can resize on the fly without any reformatting.
2. With RAID0 if one disk goes, you lose ALL the data. I actually wouldn't use raid0 for any type of server, even home. I am not sure how LVM reacts when one physical disk goes, but it can't be worst than RAID0. I actually think you could possibly recover the data on the good disk if you had LVM.

Note that with LVM you need a /boot partition outside the LVM. That is true for desktop version, I think it's the same for server.

---

### Post by perspectoff on 2012-02-14
Yeah, what you're describing is exactly LVM. Read the LVM docs.

---

