---
title: "Fixing corrupt filesystem without reformatting"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by JaySeeJC on 2013-05-24
So i decided to repartition my sustem in place today. I was fed up with there seeming to be not alternative CD for 13.04 so just went with the default encrypted lvm option on the live cd installer. When I went to examine the mostrosity this set up, i wasn't too impressed. It seemed to set up 3 real partitions, one for EUFI, one for /boot, and then the big one for lvm. In the lvm, it only created two partitions, root and swap. I wanted a third home partition so when I had the time I decided to fix that. I booted up a live CD, resized my root to as small as it would go, and made a new home. I think at this step I screwed something up because now my root is saying that it's 100% full when it's not. 

```
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  552G  530G     0 100% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          12G  4.0K   12G   1% /dev
none                         4.0G  275M  3.8G   7% /tmp
tmpfs                        2.4G  1.1M  2.4G   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                          12G   76K   12G   1% /run/shm
none                         100M   36K  100M   1% /run/user
/dev/mapper/ubuntu--vg-home  268G  197G   58G  78% /home



```

This isn't the end of the world. I can still write to the supposedly full disk fine, but I have a bunch of applications that are complaining or otherwise acting up because of it. Is there any hope for recovery? Or should I just save my home and make a new root partition?

---

### Post by Herman on 2013-05-25
Have you tried running resize2fs again? 
[[COLOR=#0000ff]How to: Resize an Encrypted Partition (LUKS)[/COLOR]]("http://ubuntuforums.org/showthread.php?t=726724") - Ubuntu Web Forums - bodhi.zazen

---

### Post by Herman on 2013-05-25
The Desktop CD can be used to create an customized encrypted logical volume layout but we have to set it up before starting the installer.
[[COLOR=#0000ff]Possible to change partition layout in ubiquity (12.10) with full disk encryption?[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2097477") - Ubuntu Web Forums.

---

