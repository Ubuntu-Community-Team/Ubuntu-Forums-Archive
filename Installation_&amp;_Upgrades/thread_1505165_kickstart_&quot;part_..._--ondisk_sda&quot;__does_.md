---
title: "kickstart &quot;part ... --ondisk sda&quot;  does not work"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by bchill on 2010-06-08
Hello,

If I speciffy '--ondisk', I get the complaint about not having a /boot partition. Say "continue" causes a failure because no physical disks have been included in the logical volumes.

If I leave off "--ondisk sda", the kickstart works. That's not really practical in certain cases.

Am I missing something?

Brian

--------------------------------------------------------------
.
.
zerombr yes
clearpart --all --initlabel
part /boot --fstype ext3 --size 128 --ondisk sda
part pv.1 --size 128 --grow --ondisk sda
volgroup VolGroup00 --pesize 32768 pv.1
logvol / --fstype ext3 --name LogVol00 --vgname VolGroup00 --size 1024 --grow
logvol swap --fstype swap --name LogVol01 --vgname VolGroup00 --size 1024
.
.
.

---

