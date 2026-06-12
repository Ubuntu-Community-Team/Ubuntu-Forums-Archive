---
title: "Problems With Multipath+LVM After Reboot"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by CharlesT423 on 2014-11-17
I'm having a problem I can't seem to resolve in regards to an LVM with two PVs: one a physical disk in the server (via a hardware RAID card) and the other through an iSCSI SAN connection.  I originally setup the LV on just the physical disk and then a few days ago I added in more space via the iSCSI SAN, which was using /dev/dm-5 as the PV.  I did a kernel upgrade last night and rebooted the server, and now I can't get the LV to work.  After the reboot the device changed from /dev/dm-5 to /dev/dm-4 (which *shouldn't* matter, but it seems to) and when I run vgchange -a y to scan the volumes I get the following errors:

On the command line:
# vgchange -a y
  device-mapper: reload ioctl on  failed: Invalid argument
  1 logical volume(s) in volume group "sasdrives" now active
  2 logical volume(s) in volume group "db1" now active

 in dmesg:

[  422.117201] device-mapper: table: 252:5: linear: dm-linear: Device lookup failed
[  422.117259] device-mapper: ioctl: error adding target to table


252:5 corresponds to /dev/dm-5  Now the file /dev/dm-5 exists, but it does not show up in multipath -ll or dmsetup ls/dmesetup table.  Removing the file doesn't make the error go away.  I've updated the filter in /etc/lvm/lvm.conf to exclude dm-5 but that doesn't seem to make a difference.  The issue seems to be that /dev/dm-5 doesn't point to an actual device and the kernel won't reload the LVM tables if it can't read that device.  Simply adding new drives to the system doesn't help because they become dm-6/7 instead of dm-5.

Any ideas?

---

### Post by nerdtron on 2014-11-17
What is the output of the following commands?
```
sudo pvscan
sudo vgscan
sudo lvscan

```

---

### Post by CharlesT423 on 2014-11-17
All the LVM stuff looks good, other than the "no device table" output from lvs.  It seems to have something to do with this phantom device map (/dev/dm-X) that gets created after I connect to the iSCSI SAN on boot.  I was able to get things going by disconnecting from the iSCSI SAN, clearing the multipath table, then reconnecting.  I would still like to know how to fix it so that the machine comes up properly at boot though...  I'm not brave enough to try a reboot right now since the machine is locked in a server room I don't have access to at the moment.

 For anyone else who has this trouble, here are the commands I entered:

iscsiadm -m node --logout
vgchange -a y
multipath -F
vgchange -a y
iscsiadm -m node --login
vgchange -a y

And here is the output of all the LVM check commands when it was broken:
```
[09:09:13]root@db1 ~ # pvscan 
  PV /dev/sdb1   VG sasdrives   lvm2 [2.45 TiB / 0    free]
  PV /dev/dm-5   VG sasdrives   lvm2 [1024.00 GiB / 0    free]
  PV /dev/sda2   VG db1         lvm2 [29.39 GiB / 0    free]
  Total: 3 [3.48 TiB] / in use: 3 [3.48 TiB] / in no VG: 0 [0   ]

[09:09:17]root@db1 ~ # vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "sasdrives" using metadata type lvm2
  Found volume group "db1" using metadata type lvm2

[09:09:22]root@db1 ~ # lvscan
  ACTIVE            '/dev/sasdrives/data' [3.45 TiB] inherit
  ACTIVE            '/dev/db1/swap' [7.45 GiB] inherit
  ACTIVE            '/dev/db1/root' [21.95 GiB] inherit

[09:09:27]root@db1 ~ # dir -d /dev/sas*
ls: cannot access /dev/sas*: No such file or directory

[09:09:34]root@db1 ~ # vgchange -a y
  device-mapper: reload ioctl on  failed: Invalid argument
  1 logical volume(s) in volume group "sasdrives" now active
  2 logical volume(s) in volume group "db1" now active
[09:09:40]root@db1 ~ # lvs
  LV   VG        Attr      LSize  Pool Origin Data%  Move Log Copy%  Convert
  root db1       -wi-ao--- 21.95g                                           
  swap db1       -wi-ao---  7.45g                                           
  data sasdrives -wi-d----  3.45t                                           

```

---

