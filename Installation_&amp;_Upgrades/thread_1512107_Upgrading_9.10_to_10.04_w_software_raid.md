---
title: "Upgrading 9.10 to 10.04 w/ software raid"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by rmcd on 2010-06-17
I have an existing 64-bit 9.10 system with three disks. /dev/sda and /dev/sdb are in a software RAID 1 array, with 6 partitions. Four are /boot, /, /home, swap, and two are empty. I did this to provide a choice between a new OS install and an in-place upgrade to later ubuntu versions.

My question: what is a safe procedure to upgrade to (or newly install) 10.04 and insure that it will work with RAID? I'm concerned by the reports of unbootable systems, and I know from building this machine that Grub 2 and RAID seemed a little flaky together, at least under 9.10.

I upgraded a Debian Lenny machine with software RAID to Squeeze and it installed grub 0.97 as the default bootloader, with a link to boot via Grub 2. This is a great approach, especially since booting via Grub 2 hangs that machine :-(  Will the 10.04 installer do the same thing, i.e. stick with grub 1 by default? Are there any things to watch out for during the install?


Thanks very much for any advice.

Bob

---

