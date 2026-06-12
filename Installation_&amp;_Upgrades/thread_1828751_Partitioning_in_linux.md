---
title: "Partitioning in linux"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by waqas300 on 2011-08-19
hi, 
   Can anyone please help with defining linux partitions.

Are following enough or what else changes to be made?

root
boot
swap

how much are recommended for each of these?

---

### Post by dave01945 on 2011-08-19
i use 3 partitions at the moment 1 for root 1 for home and 1 swap my swap is 1gb but i have never used this having 4gb of ram.

when i first installed linux i only used 2 i for root and 1 for swap i have a separate 1 for home now because if i want to change distro or do a clean install i can do so without affecting my home files on the separate partition

my root partition is 40gb and im using under half of that

---

### Post by oldfred on 2011-08-19
I do not recommend a separate /boot for standard desktops. Servers or very old computers may need it.

As dave01945 suggested, / (root), swap & /home is a better partitioning scheme as all you user settings & data is in /home. If you ever want to do a clean reinstall you can reuse your existing /home and not lose settings & data (as long as you do not reformat it).

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

