---
title: "Install hangs at Waiting for Root Filesystem Ubuntu 8.04"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2008-05-02
The Live CD of Ubuntu 8.04 loads and works with no problems.

When I install however (using the install icon from live desktop), all appears well, I am installing / on sda11  /home on sda12 and swap file is sda6. All files appear to copy (but there is no final message that all is installed).

On reboot, I see what looks like a BBC testcard (coloured rectangles, various line sizes) and in the centre boot messages. However boot hangs at waiting for root filesystem.

After some time around 10 minutes I reach a limited initramfs shell, no partitions have been mounted and no /var/log/messages created.

What changes between the live CD and a HD install?

More information:
I have 2 hard drives, (both UDMA). The first HD has 23 partitions, I wonder if the libata library is not coping with partitions. Also partition
2 is  (BF) Solaris and partition 3 is UFS for FreeBSD.
I change these file systems to native linux  (type 83) before installing
any linux using gparted.

The 2nd hard drive has Vista on partition 1 and the rest free space.

Is there a way to disable libata emulation, or any work around to install ubuntu? I had the same problem with 7.04 and 7.10, my solution was to install my own kernel, without libata emulation.

Thanks in advance

---

