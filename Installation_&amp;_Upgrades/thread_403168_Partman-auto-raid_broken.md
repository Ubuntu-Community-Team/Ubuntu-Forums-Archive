---
title: "Partman-auto-raid broken"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by jrobison on 2007-04-06
I am trying to install Feisty (2007-04-05 cd image build) with netboot, so far everything works except RAID, which was supposed to be fixed for Feisty.

I have 2 drives and my recipe is as follows:

d-i partman-auto/expert_recipe string \
multiraid :: 75 100 120 raid $primary{ } method{ raid } \
. \
2000 2000 2000 raid $primary{ } method{ raid } \
. \
23000 240000 1000000 raid $primary{ } method{ raid } \
.


d-i partman-auto-raid/recipe string \
1 2 0 ext2 /boot /dev/sda1#/dev/sdb1 \
. \
1 2 0 swap - /dev/sda2#/dev/sdb2 \
. \
0 2 0 ext2 / /dev/sda3#/dev/sdb3 \
.

I have tried using this on just one line, but to no affect. The partman log looks fine, no errors that I can see, but this log is not really laid out the best. I will attach the log to this thread as soon as I try to install again.

I would really love some help on this as I need to have an automated deployment system or Ubuntu will no longer be a viable option for me.  Someone has to have some information on this, I can imagine alot of people are using Ubuntu Server, it is a great package but RAID autoconfig for a server package should have been a requirement as SATA RAID has become very popular as of late especially with SuperMicro and Rackable machines.


Please let me know if there is any information that is needed that I did not include.


-Joel Robison
Systems Engineer

---

