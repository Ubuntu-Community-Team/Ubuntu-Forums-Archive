---
title: "Cannot install on 120gig free space drive"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by lsatenstein on 2008-05-03
I would like to describe my system and then indicate the problem.

Intel dual core system with 3.5gig memory.


disk1  SATA 320 gig, partitioned to  150gig Fedora 8
disk1  Second Partition   partition 2   **  FREE SPACE      where I want to install**

disk2  SATA 250 gig                         Fedora 9 Preview

disk3  IDE  150 gig  Front partitions       XP
disk3  IDE  100 gig  Back Partition         PCLINUXOS

BIOS SETTING      BOOT DRIVE Disk1

I run through the install program, and if I take the defaults, it wants to install in disk3 partition 2, replacing pclinuxos

If I change the settings to indicate to use the free space, it wants to overwrite one of the other working linux systems.

If I tell it to go manually, then it does not let me repartition the free space, but wants me to make it one of the mounted points (example / )

In the past, when I tried it with 7.10, Ubuntu destroyed grub so that nothing booted. ( I even tried unplugging the two hard drives that I did not want it to touch, and that did not work).

I would like to use ubuntu, for the look and feel, and because of the significant user group.


Any suggestions please?  I accept emails.

Thanks in advance.

Mr. Leslie
(grandfather of 3)

---

### Post by Pumalite on 2008-05-03
Go Manual and choose the second partition of the first disk.(free space)

---

