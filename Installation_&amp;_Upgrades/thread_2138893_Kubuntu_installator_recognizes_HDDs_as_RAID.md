---
title: "Kubuntu installator recognizes HDDs as RAID"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by nullguy on 2013-04-25
I was running Kubuntu liveUSB on a machine with two identical HDDs, and everything went fine untill disk management settings appeared.
The problem is that Kubuntu recognizes both HDDs as one RAID array, and asks to install itself on one 640GB(320+320) partition.
In 'Manual' config tab it shows wrong partitions and some random looking stuff. I'm getting something like (RAID1_hjhhhhib-something-something, with two partitions in it, and RAID2_hjhh-something-something showing as empty 320GB space, instead of /dev/sda and dev/sdb). Originally,  first HDD have ~100MB and ~300GB NTFS partitions, while the second one have 100GB and 200GB NTFS partitions.
Kubuntu does not recognize those filesystems and can't calculate % of space used on it, and i don't want to loose data stored on those partitions in case if installation goes wrong, so basically i can't even install it.
 Checked BIOS settings, it does not have anything RAID-related enabled, and preinstalled Win7 doesn't seem to use RAID neither, so I have no idea what causes that issue. How can i install my distro on the 100GB partition(with formating to ext4) without harming other ones?

---

### Post by darkod on 2013-04-25
If you are sure you are not running raid (or that the manufacturer somehow sent the machine with raid setup), you can try removing meta data from both disks. That should make the problem go away:
```
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb
```

But before running that from live mode, I would investigate the machine setup. Maybe it is connected to raid somehow, with small SSDs for caching, etc.

---

