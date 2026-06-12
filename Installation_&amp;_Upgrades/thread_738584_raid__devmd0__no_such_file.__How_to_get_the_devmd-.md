---
title: "raid : /dev/md0 : no such file.  How to get the /dev/md*-files"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2008-03-28
I installed  a raid on ubuntu 7.10 with mdadm (--create, I did not change mdadm.conf) and it worked fine: /dev/md0 was up and running. I rebooted and it was still up and running.

Two weeks later I had to reboot again and suddenly my raid was not started anymore. I couldnt even start it anymore, cause:

#mdadm -A /dev/md0 /dev/sdc2 /dev/sdb2
mdadm: error opening /dev/md0: No such file or directory 

I turned out that there isnt a single /dev/md*  anymore.

How comes?  And how to get it back? which package provides this files? Earlier the raidtool or raidtool2-packge did it, but these are depreceated and not available any more.

Which package should provide these files now???

Some entries in this forum suggest that mdadm itself creates the /dev/md-files, but obviously it doesnt.

How do I get this /dev/md-files ??

thnx
peter

---

### Post by davemc on 2008-04-06
Same problem booting with Gutsy live cd to a system that had severe drive problems.

root@ubuntu:/dev# ls /dev/md0
ls: /dev/md0: No such file or directory

This fixed the problem...

The normal way of starting an array at boot time is by describing the
array (usually by UUID) in mdadm.conf and letting mdadm find the
component devices with "mdadm --assemble --scan".

root@ubuntu:/# mdadm --assemble --scan
mdadm: /dev/md2 has been started with 2 drives.
mdadm: /dev/md1 has been started with 1 drive (out of 2).

root@ubuntu:/# cat /proc/mdstat
Personalities : [raid1] [raid0] [raid6] [raid5] [raid4]
md2 : active raid1 hdb2[0] hda2[1]
      731447360 blocks [2/2] [UU]

md1 : active raid1 sda1[1]
      312568576 blocks [2/1] [_U]

unused devices: <none>

---

