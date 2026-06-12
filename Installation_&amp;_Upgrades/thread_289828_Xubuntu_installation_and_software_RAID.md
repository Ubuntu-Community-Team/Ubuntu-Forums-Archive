---
title: "Xubuntu installation and software RAID"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by quzqo on 2006-10-31
Hello,

Based on a xunbuntu 6.10 alternative x86 CD-Rom, I tried to install with  all the partitions in software RAID (RAID 1, except for swap).

I have 6 RAID + 1 swap partitions on each SCSI disk previously installed with a fully functionnal Debian distribution :
[FONT="Lucida Sans Unicode"]- *primary* /boot (sd[ab]1 bootable)
- *primary* <swap> (sd[ab]2)
- *primary* / (sd[ab]3)
- *extended* /usr (sd[ab]5)
- *extended* /usr/local (sd[ab]6)
- *extended* /var (sd[ab]7)
- *extended* /tmp (sd[ab]8)
- *extended* /home (sd[ab]9)[/FONT]

During the installation process, all the RAID and swap partitions  have been detected by the partitionning tool and are well tagged (RAID or swap) but...
When I tried to configure the first RAID partition, the installation process freezes after the validation of the 2 active disk and 0 spare disk (default choice).
There is no message, just an empty blue-screen with a blink-cursor in the down-left corner of the screen.

If someone can help me to solve this I would be pleased to try Ubuntu desktop.

I will try with a standard Ubuntu 6.10 Alternative x86 But I am afraid that the problem remains whole

In advance, thank you for your answers.

---

