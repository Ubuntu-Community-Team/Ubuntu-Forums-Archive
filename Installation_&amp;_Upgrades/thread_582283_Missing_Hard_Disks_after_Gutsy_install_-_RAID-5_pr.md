---
title: "Missing Hard Disks after Gutsy install - RAID-5 problem"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by ballardb on 2007-10-19
OK,  luckily I had a spare 320GB to try a clean Gutsy Gibon server install...

Old 6.10 Install runs    4 320GB drives    as raid-5 using mdadm. and a primary OS drive also on a 320GB drive.

Installed new server on to new drive (all raid drives disconnected..cant risk corruption).  All installed,  connect all drives, power up,  try   mdadm --assemble /dev/md0  /dev/sdb /dev/hda /dev/hdb /dev/hdc
and it fails


Then I find that the drives are not listed in  /dev    no sign of any of them (well except /dev/sda, my OS drive)

So I realize this isnt an mdadm issue but an OS install issue.... I will continue to track but is this a common problem of late?  Forums searches suggest otherwise, but adding drives should just turn up right?

---

### Post by ballardb on 2007-10-19
OK further investigation shows that my 6.10 install had my drives sorted as:


/dev/sda  (my primary OS drive)
/dev/sdb  
/dev/hda
/dev/hdb
/dev/hdc


now I have 5  /dev/sd  devices   /dev/sda  to /dev/sde      with my OS drive shopwing up as /dev/sdd   what the???? since when do  old ATA IDE drives get labeled /dev/sd*  ??   maybe im old old school on this but im still expecting /dev/hd*

im too worried to risk trying to    assemble my software raid on this 7.10 install.... and what with what ive been reading from other people... im moving away to something safer like CentOS again....

---

