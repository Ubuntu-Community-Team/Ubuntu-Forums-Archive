---
title: "syslog Floods with   device appeared twice with different sysfs paths"
date: 2017-06-02
forum: Installation &amp; Upgrades
---

### Post by redhat22 on 2017-06-02
My syslog Floods with notich warnings about my hard disks every 5 minutes there are 4 disks working in raid 1 witch multiple partitions.
The system is ***[COLOR=#6a6a6a]Ubuntu Server[/COLOR]*** 16.04.2 LTS.
i have searcht for the problem it is described here.
[https://github.com/systemd/systemd/commit/071e0b8b3a698e73bcaecba09ffccab5553d2365](https://github.com/systemd/systemd/commit/071e0b8b3a698e73bcaecba09ffccab5553d2365)

And gives a solution for a pach but i have no idea how to aply the pach.
i hope someone can help.

I have past a line from the log file.

dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sda/sda1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:1/2:0:1:0/block/sdb/sdb1

thanks in advance.

jasper

---

### Post by Ackis on 2017-06-02
I'm having a similar issue, except I'm not running a RAID array.

I did find this: [https://ubuntuforums.org/showthread.php?t=2275068](https://ubuntuforums.org/showthread.php?t=2275068)

Might be able to help you out? At the very least there's some commands you can run to provide more information.

---

### Post by redhat22 on 2017-06-03
i have seen this thread the problem is on a active server so i cant destroy the raid.
I have tried to remove one disk reformat and label it but gave no diverence  the raid labeled it again.

---

