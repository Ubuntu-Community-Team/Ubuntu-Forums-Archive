---
title: "Two partitions mounted on &quot;/&quot;  ??"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by flemur13013 on 2011-04-30
Mostly FYInterest - 

With two primary ext4 partitions, one a backup copy of the other, which has the OS. They're the 1st two partitions on the disk.  Only the 1st partition was listed in fstab, the copy is rarely used and it'd mount to /media/somenumber (the UUID?)

I'd been fooling around installing fluxbox, openbox, updating wine, and some similar stuff, and noticed that when I rebooted, the things I'd just installed were gone. Then I'd log out/in and they'd be back, but wine was an older version and some changes to files were gone.

Anyway, gparted showed that the **two partitions were both mounted as "/" **and neither could be unmounted while running (fixed w/LiveCD;  deleted the copy partition, then merged them). 

Although I'm not going to try and duplicate this, it seems like I got one partition as the real "/" when I rebooted but it'd change to the other when I logged out and back in.  In either case they'd both be mounted as "/".

How this happened I have no idea...

---

