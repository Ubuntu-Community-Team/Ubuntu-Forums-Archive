---
title: "ubuntu 10.04 LVM partitioning query (noob!)"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by maja_z on 2011-03-05
Hi!
I'm planning a clean install of 10.04 (64bit) (for reasons of long term support not 10.10) on my desktop. I'm trying to plan my partitioning ahead so I just wanted to run this by you to check it made sense!

I'd like to use LVM, so I already know I need the alternate installation CD and have had a look through this incredibly usefull guide (hope it works for 10.04 as well!): [http://www.linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/ ]("http://www.linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/")

Here's my provisional plan:

/boot     200 MB
LVM (the rest  on a 640 Gig drive) to include:
swap     8 GB
/           50 GB
/home   300 GB

So my questions are:
1. are the size allocations reasonable? If I understand correctly I should have enough to get my system running and leave the unallocated space for later if it is needed in /home or wherever. Or should I just make /home as large as it  goes? 
2. Does this partitioning scheme make sense in case I some time in the future get santa to buy me an ssd. Can I then move the root onto it easily? Should root be in the LVM?
3. Which filesystem should I use? ext4 or Reiserfs or something else? 

I'm not a particularly demanding user, I would just like a setup that will last me a while and can be upgradable (e.g. adding new disks without a reinstall..). Am I going about this OK? 
Thanks!

Maja.

---

