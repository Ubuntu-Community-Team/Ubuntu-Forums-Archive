---
title: "Edgy-&gt;Feisty: RAID1 doesn't work anymore"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by tr2 on 2007-04-25
Hi all

Under Edgy the two disks I use for RAID1 were detected as /dev/hda and /dev/hde. hda1 and hde2 made up /dev/md0 mounted as / and hda2 and hde3 together were /dev/md1 mounted under /home. The /boot partition is non-RAID and only on one disk. After upgrading to Feisty the disk formerly known as /dev/hde is now /dev/sda (probably because it's on a separate IDE-Adapter). Upon booting the RAID-disks don't get formed correctly:

From dmesg you can see that at first only /dev/sda is detected and used for the RAID:
```
[    5.196000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.196000]  sda: sda1 sda2 sda3 sda4
[    5.200000] sd 0:0:0:0: Attached scsi disk sda
[    5.204000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.452000] md: bind<dm-0>
[    5.464000] raid1: raid set md0 active with 1 out of 2 mirrors
[    5.480000] md: bind<dm-1>
[    5.492000] raid1: raid set md1 active with 1 out of 2 mirrors
```
Later /dev/hda get's initialized, but too late for RAID:
```

[   19.276000] hda: max request size: 512KiB
[   19.280000] hda: 234493056 sectors (120060 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   19.284000] hda: cache flushes supported
[   19.284000]  hda: hda1 hda2 hda3 hda4 
[   19.308000]  hda5 hda6 hda7 >
```
The commands
```
mdadm --add /dev/md0 /dev/hda1
mdadm --add /dev/md1 /dev/hda2
```
correctly rebuild the two RAIDs. I've added the line
```
DEVICE /dev/hda*, /dev/sda*
```
to my /etc/mdadm/mdadm.conf file, but to no avail. :( 

Any ideas would be very welcome.

Thanks, tr2.

EDIT: BTW: The superblocks of the RAID partitions that belong together do show the same UUID.

---

### Post by idefixx on 2007-05-06
Just wanted to say that I have the exact same problem. One of my raid arrays are built from hda and sde. For some reason the raid system activates the array before hda is initialized. Either hda is initialized too late or the raid code decides prematurely to activate the array without finding all possible partitions. 
Quite annoying...

EDIT: Filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/112923](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/112923)

---

### Post by tr2 on 2007-05-06
Ah, my bad I haven't responded to this thread anymore. I've found the bug: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177")

---

### Post by idefixx on 2007-05-07
Thanks, that worked. (Added sleep 30 in the initramfs init script as described in [http://ubuntuforums.org/showpost.php?p=2236181&postcount=5](http://ubuntuforums.org/showpost.php?p=2236181&postcount=5))

---

