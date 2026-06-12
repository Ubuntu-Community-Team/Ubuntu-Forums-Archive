---
title: "6 partitions? ... No Ubuntu"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by Rebootin on 2013-02-06
Help!

I am trying to install Ubuntu 12.04 on my wifes new HP Pavilion G7. The computer came with Windoze 8 installed and I want to dual boot to Ubuntu.

I used Win disk manager and shrunk the primary partition and added a 5 gig partition.
I then fiddled with the bios and **FINALLY** got the computer to boot from CD.
I then installed Ubuntu 12.04 desk. No problems.

When I rebooted, it booted to Windoze (no Ubuntu). I then used disk manager to look at the hard disk and found:

**0 Disk Basic 698.51 Gb**
1. Healthy (Recovery Partition) - 400 mb
2. Healthy (EFI System Partition) - 260 mb
3. (C:) Healthy (Boot, Page File, Crash Dump, Primary Partition) - 658.03 Gb NTFS
4. (F:) Healthy (Primary Partition) - 9.11 Gb RAW
5. Healthy (Primary Partition) - 5.89 Gb
6. Recovery (D:) Healthy (OEM Partition)

I thought you could only have 4 partitions on a disk ???
Where did Ubuntu go ???
Where do I go from here ??? I've read that Windoze is sensitive about messing with partitions.

In review, I realize I didn't format the new partition and I think that is part of the problem.

What should I do now to fix this ???

---

### Post by oldfred on 2013-02-06
Thread Closed. Duplicate.
[http://ubuntuforums.org/showthread.php?t=2113144](http://ubuntuforums.org/showthread.php?t=2113144)

---

