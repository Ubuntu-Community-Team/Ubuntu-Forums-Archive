---
title: "[resolved] Grub or some other problem"
date: 2004-12-07
forum: Installation &amp; Upgrades
---

### Post by lameth on 2004-12-07
Hello all I just installed ubuntu 4.10 and I'm having a boot problem.

System info:

MSI K8T Neo2 FIR with a AMD64 3500 cpu
1 gig of ram
two hard drives:
First drive 27 gig eide ata drive partitioned as follows:
partition 1 roughly five gigs mounted as /win98
partition 2 roughly 10 gig mounted as /
partition 3 130 mb swap
partition 4 roughly 11 gig mounted as /home
Grub is installed on this drive's mbr
Second drive 60 gig eide ata drive partitioned as follows
partition 1 60 gig mounted as winxp
The windows boot loader is mounted on the second drive's mbr

After the base install of Ubuntu the computer restarted to the grub bootloader, neither windows partitions were recognized. During the intitial boot process for what ever reason fsck was initiated and tried to scan my /winxp partition. Text scrolls very rapidly on the screen with messages about "start cluster beyond limit" until fsck stops and I'm prompted to either fix the disk manually or press Control-D to exit the shell and resume the boot process. Which after pressing control-d the boot process finished and linux starts.

I've been running slackware 10 for months and /winxp was never scanned by fsck during the boot process. And to be perfectly blunt I don't want fsck scanning either /win98 or /winxp at start up.

Is this a problem with grub or is there some other script or file at work here?

If it helps I looked at syslog and saw this entry....
Dec  7 23:40:02 localhost kernel: fsck.vfat[1392]: segfault at 0000000a9669e010 rip 0000000000404e56 rsp 0000007fbffff880 error 4

When I was using slack LILO never had a problem booting me over to the windows boot loader.

Thanks for any advice you can give

PS
Almost forgot I'm running the 64 bit version of ubuntu 4.10

---

