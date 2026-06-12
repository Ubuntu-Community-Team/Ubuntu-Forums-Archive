---
title: "Partitioning help for VMware server"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by matt_b on 2007-03-15
Hi,

I am going to be using Ubuntu 6.06 server as the host OS on my PowerEdge 4600 server which will be running only VMware server. This server has 3GB RAM, two 9GB disks in RAID1 and five 18GB disks in RAID5 (72 GB usable). What I want to do is configure the partition table to get the best performance out of my two disk arrays.

From reading the VMware server admin guide and other sites, it suggests that my swap and temp partition be set to 1.5 times the physical RAM ([http://searchservervirtualization.techtarget.com/tip/0,289483,sid94_gci1241828,00.html)](http://searchservervirtualization.techtarget.com/tip/0,289483,sid94_gci1241828,00.html)). For a one-disk server the partition guide suggests:
[B]
       /boot,  200 MB,      ext3, boot flag
       /,          6 GB,           ext3
       swap, 4.5 GB,        swap
       /tmp,   4.5 GB,        ext3
       /var,   rest of disk,  ext3[/B]

As I have two arrays I think I should put the boot, swap and temp on my 9GB array, and / on my 72GB array, as follows:

[B]       ARRAY 1:
       /boot,   200MB,   ext3, boot flag
       /swap, 4.5GB,     swap
       /tmp,    4.5GB,     ext3

       ARRAY 2:
       /,   72GB,   ext3[/B]

Would this give me the best disk performance? Would it be wise to limit / to 6GB and create /var with the most space, similar to the first one-disk suggestion?

Thanks
matt_b

---

### Post by matt_b on 2007-04-07
Still after some help on this one, but a simpler question:

Would it be better to put swap on a different array, or /tmp? I'm thinking that isolating swap would give me the best performance.

Also, can I mount /tmp in two places and specify which to use first?

Thanks
matt_b

---

