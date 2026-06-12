---
title: "Fail back to 18.04 on RAID mirror."
date: 2022-04-12
forum: Installation &amp; Upgrades
---

### Post by john412 on 2022-04-12
I am working to create a process to do a dist upgrade from Ubuntu 18.04 to 20.04 on a few thousand remote servers. The rollout will take several months. I created a local mirror for them to pull from so that all sites will get the same versions of packages. I have a working POC for an unattended dist upgrade that works quite well. I have been asked about fail back (to 18.04) in the event of a failure. We have a RAID mirror on 2 drives and a LUKs volume on md0. My initial thought was that I would fail and remove sdbx from the RAID arrays and then boot to the second drive if needed. However, I have been unable to do so. I went so far as to assemble the boot volume md2 with a new MD-UUID, then updated the grub entry for 4.15 with that MD-UUID and installed it on sda.

Does anyone have any ideas on how  we can fail back to the other drive?

This is our file system layout. I left out md1/vg1 because that is an empty staging volume.

```
sda                       8:0    0 465.8G  0 disk
&#9500;&#9472;sda1                    8:1    0     1G  0 part
&#9474; &#9492;&#9472;md2                   9:2    0  1024M  0 raid1 /boot
&#9492;&#9472;sda2                    8:2    0 120.1G  0 part
  &#9492;&#9472;md0                   9:0    0   120G  0 raid1
    &#9492;&#9472;cryptroot         253:1    0   120G  0 crypt
      &#9500;&#9472;vg0-swap        253:2    0   1.9G  0 lvm   [SWAP]
      &#9500;&#9472;vg0-root        253:3    0  44.6G  0 lvm   /
      &#9500;&#9472;vg0-appl        253:4    0     8G  0 lvm
      &#9474; &#9492;&#9472;drbd0         147:0    0     8G  0 disk  /appl
      &#9500;&#9472;vg0-db          253:5    0     5G  0 lvm
      &#9474; &#9492;&#9472;drbd1         147:1    0     5G  0 disk  /var/lib/postgresql/10/main
      &#9500;&#9472;vg0-backup_root 253:6    0  44.6G  0 lvm
      &#9500;&#9472;vg0-backup_appl 253:7    0     8G  0 lvm
      &#9492;&#9472;vg0-backup_db   253:8    0     5G  0 lvm
sdb                       8:16   0 465.8G  0 disk
&#9500;&#9472;sdb1                    8:17   0     1G  0 part
&#9474; &#9492;&#9472;md127                 9:127  0  1024M  0 raid1
&#9492;&#9472;sdb2                    8:18   0 120.1G  0 part
  &#9492;&#9472;md0                   9:0    0   120G  0 raid1
    &#9492;&#9472;cryptroot         253:1    0   120G  0 crypt
      &#9500;&#9472;vg0-swap        253:2    0   1.9G  0 lvm   [SWAP]
      &#9500;&#9472;vg0-root        253:3    0  44.6G  0 lvm   /
      &#9500;&#9472;vg0-appl        253:4    0     8G  0 lvm
      &#9474; &#9492;&#9472;drbd0         147:0    0     8G  0 disk  /appl
      &#9500;&#9472;vg0-db          253:5    0     5G  0 lvm
      &#9474; &#9492;&#9472;drbd1         147:1    0     5G  0 disk  /var/lib/postgresql/10/main
      &#9500;&#9472;vg0-backup_root 253:6    0  44.6G  0 lvm
      &#9500;&#9472;vg0-backup_appl 253:7    0     8G  0 lvm
      &#9492;&#9472;vg0-backup_db   253:8    0     5G  0 lvm

md2 : active raid1 sda1[0] sdb1[2]
      1048512 blocks super 1.0 [2/2] [UU]

md0 : active raid1 sdb2[2] sda2[0]
      125869733 blocks super 1.2 [2/2] [UU]
```

Disclaimer: I did not create this setup. There is no need to tell me it is wrong. I already know.

---

### Post by TheFu on 2022-04-12
If you don't have out-of-band IPMI/DRAC/RIBLO, no way would I attempt this, unless someone could be in the remote location with sufficient skills to bring up a base OS and I could get access to reload it from scratch.  Obviously, full, know-we-can-restore backups are mandated BEFORE starting. RAID never replaces backups. Never.  There are times when RAID fails and the only answer is to wipe all the disks and recreate the RAID from scratch.

Imaging less than 10% of these systems have a failure. That's still a huge number of required visits. Even just 1% is hard for a small team.

BTW, you know that mdadm isn't needed for RAID if you use LVM, right?  LVM2 supports RAID using lvconvert options. Works well in my limited testing.

---

