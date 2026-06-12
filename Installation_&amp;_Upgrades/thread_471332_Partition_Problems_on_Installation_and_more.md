---
title: "Partition Problems on Installation and more"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by xi'an on 2007-06-11
All was going well until one evening I clicked on Applications and all the toolbars disappeared and that was all she wrote.  When I turned off my computer I got a "grub error 19" message.  Checked out the forums and seemed to have that settled.  I tried to reinstall Ubuntu (this was 6.10) using the live CD.  After successfully doing so, I tried to upgrade to 7.04.  Back to the "grub error 19" message.

So, I tried to install 7.04 from a live CD.  Downloaded, checked disk for errors, booted up and everything looked good.

However...

When it got to partitioning here are the results:

First I tried Guided - Use entire disk.  I received this error message, "Attempt to mount system with type ext3 in IDE2 master, partition #1 (hdc1) at / failed."

I clicked on continue and got the screen with the slider: "Resize IDE3 master, partition #7 (hdc3) and use freed space ."  Got this message,"Attempt to mount system with type ext3 in IDE2 master, partition #7 (hdc7) at / failed."

Next I tried Guided - Use largest continuous free space.  Got this message, ""Attempt to mount system with type ext3 in IDE2 master, partition #5 (hdc5) at / failed."

Next I tried Manual.  Got this message, "Attempt to mount system with type ext3 in IDE2 master, partition #1 (hdc1) at / failed."

I have two hard drives on my computer: one I had windows xp installed on, and the other had Fedora (originally).  All worked well, but I looked at Ubuntu and liked it better than Fedora so I switched.  After I installed Ubuntu, I no longer had an option at startup to open windows, but that did not particularly bother me because I wanted to switch over to Ubuntu entirely anyway.

An anomaly, and, maybe, the problem?  Both hard drives are 80 GB.  But when I get up to the partition stage in installing Ubuntu I am shown one drive of 160 GB.

I am not entirely new, but it would be most helpful it I was given very basic step-by-step directions if anyone has answers to these problems.  

Thanks.

---

