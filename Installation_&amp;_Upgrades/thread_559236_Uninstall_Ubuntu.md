---
title: "Uninstall Ubuntu"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by cheluus on 2007-09-24
In my new ACER 5630 laptop completely removed windows vista and installed ubuntu 7.0.4 and now planning to install vista using recovery CD, And i am not able to install vista any more. starts disk loading and while partitioning getting error. How it install vista using recovery CD. ubuntu is great, but  to run winrunner/load runner/qtp software, windows required. Please do the needfull. Thanks alot in advance.

---

### Post by Shazaam on 2007-09-24
Hmm. When you installed Ubuntu did you use the ENTIRE drive? Your pc may have had a "Rescue" partition along with Vista. Your rescue cd may need that partition to re-install Vista.
If that is the case contact ACER or buy a retail version of Vista
.
If you still have the Ubuntu livecd, boot from the livecd, open Terminal, type in
 
sudo fdisk -l

and post the output here.

---

### Post by cheluus on 2007-09-24
Thanks for reply. Yes, used complete drive option.  and  partion list

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18704   150239848+  83  Linux
/dev/sda2           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris

Thanks

---

### Post by Shazaam on 2007-09-25
Yeah everything Vista related is gone. Since it is a new pc contact ACER (or the store you bought the computer at) and they may be able to help you.

---

### Post by cheluus on 2007-09-25
Ubuntu is a freeware, and acer not support damages due to third pardy software. There is no other easy way to fix this problem. Anyway Thanks alot for ur response.

---

### Post by Shazaam on 2007-09-25
Well, you could play dumb and tell ACER that the pc crashed and the drive got wiped. After an fdisk and a format of course to get a blank drive.

---

### Post by DMcA on 2007-09-25
I have an acer laptop too, so far I've found their support department to be pretty linux friendly. There is a recovery partition  and without that I think you're right, there's no easy way to reinstall windows. However they did reinstall windows for me after taking the laptop in for repair, although the reason for the repair was a hardware rather than a software issue. I think they said if the problem was caused by software I'd installed they'd bill me for the job.

---

