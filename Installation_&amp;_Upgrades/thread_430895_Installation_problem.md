---
title: "Installation problem"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by fishamit on 2007-05-02
Hello,

im trying to install ubuntu right now, but i'm having a bit of a dillema.

i have two options - one is to install a brand new hard drive (120g) in addition to the one with windows, and install linux seperately on that drive. Is that possible? how do i make a dual boot?


the other option is of course to partition drive C.  it's already partitioned, (due to a previous red hat install which is gone long ago). so i tried installing Ubuntu on that partition, but then in that installation screen it says i havent specified "/root" or something like that. I have no clue what to do, please help!

and what is better, 2 operation systems on 2 seperate hard disks or 2 op systems on 2 partitions?(1 disk)


thank you!

---

### Post by mikewhatever on 2007-05-02
It does not matter much how you install Ubuntu. If you want it on the second HDD, partition it, formate and install, or simply let the installer to wipe the drive and do the job. If you want it on the first one, well, you need to create  root (/) and swap partitions. Make sure root is mounted as /, and swap as swap.
Here is a guide to help [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

