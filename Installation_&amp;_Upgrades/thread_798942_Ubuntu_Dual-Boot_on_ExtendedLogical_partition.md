---
title: "Ubuntu Dual-Boot on Extended/Logical partition"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Gunn3r on 2008-05-18
Hello to all.
I have a little problem regarding Ubuntu installation.
I have partitioned my laptop in the following way:

sda1 -> recovery partition (primary) -> 1.4GB
sda2 -> Vista partition (primary) -> 101GB
sda3 -> DATA partition (primary) -> 58GB
unpartitioned space ----> 71GB

Now, as you can see I have already three primary partitions and Ubuntu only allows me to create one primary partition only or one Extended partition (with x logical ones inside), so my main problem is...
Can I fully install Ubuntu 8.04 on an Extended partition (with separate logical partitions for /, /home and swap)?

Since I want to fully install Grub on the / partition (and use EasyBCD on Vista for bootloading the 2 OS's), will Grub recognize the separate partitions (within the Extended one) with no problems?

Ty for all the answers and help.

---

### Post by tamoneya on 2008-05-18
you are going to have to make your fourth partition extended and then put /, /home and swap as logical partitions inside. GRUB should be able to handle this fine though.  The only thing that would have trouble in an extended partition is vista(windows in general).  It typically has trouble unless it is on a primary partition.

---

