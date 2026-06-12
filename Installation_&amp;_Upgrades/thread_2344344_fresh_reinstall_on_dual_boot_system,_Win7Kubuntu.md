---
title: "fresh reinstall on dual boot system, Win7/Kubuntu"
date: 2016-11-24
forum: Installation &amp; Upgrades
---

### Post by horseatingweeds2 on 2016-11-24
Hi,

I'm trying to do a fresh install of Kubuntu (64 bit) over a partition currently containing Kubuntu (32 bit). The trouble is, when I get to the disk setup part of the installation, I can't figure out how to specify that the install should happen on that partition, and not the Windows partition. 

Do I need to use the partition editor first and delete the partition? 

Thanks

---

### Post by ajgreeny on 2016-11-24
Use then "Something Else" option and all partitions on all disks will show.

You can then click on the appropriate partitions and choose "Change" to create the new root / partition, choose to Use as ext4, mountpoint as / and lastly choose to format it by ticking the box if it is not selected by default. The old swap partition should be found and used automatically.

If you have a separate /home partition choose that and give it the /home mountpoint, but most importantly, do not select the format tick box or you will lose everything in it.

---

