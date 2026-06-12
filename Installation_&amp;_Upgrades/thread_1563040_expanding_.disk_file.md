---
title: "expanding .disk file"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by Jeroen De Dauw on 2010-08-28
I installed Kubuntu 10.04 a while back from Windows on an 150GiB NTFS partition. The Kubuntu (EXT4 I guess) filesystem is only 30 Gib big, and is located at ```
D:\ubuntu\disks\root.disk
``` in Windows. Obviously I want to use the whole 150 GiB of my partition, and I also don't want to re-install and lose my current Kubuntu setup. So how do I fix this?

---

### Post by oldfred on 2010-08-29
If you are liking Ubuntu, you should consider converting to a full install.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

You can copy all your /home into the new install. And you can make a list of all installed applications to reinstall in your new install.

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Old conversion LVPM, see Alternative Instructions 
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

