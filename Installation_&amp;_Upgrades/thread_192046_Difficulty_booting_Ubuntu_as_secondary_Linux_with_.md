---
title: "Difficulty booting Ubuntu as secondary Linux with LVM"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by grandpa-geek on 2006-06-08
I installed Ubuntu on my laptop as a secondary Linux distro (with FC5 as the primary Linux and Windows XP on there also).  I used the alternative install iso.  I created VolGroup00/LogVol03 as its partition.  I bypassed the grub install phase, because I did not want the Ubuntu install of grub to overwrite the FC5 install of grub.  I did get a message that I hand copied to put certain data into grub.conf.

I then tried to set up grub.conf.  I tried a lot of things but found no way to tell grub to mount VolGroup00/LogVol03 for the Ubuntu boot.  The messages from grub kept saying things like "can't mount partition."

My next attempt has been to copy the Ubuntu vmlinuz and initrd.img to /boot and to try to boot Ubuntu that way.  The problem now is that, although initrd.img appears to be figuring out that there are four partitions in VolGroup00, it keeps either hanging on a "waiting for root partition" message or telling me that the root= statement on my kernel line in grub.conf is not a proper root= statement.  I have tried numerous ways to formulate the root= statement, root=/dev/mapper/VolGroup00-LogVol03 (per the message during installation), root=/dev/VolGroup00-LogVol03, root=/dev/VolGroup00/LogVol03, and many others.

The grub manual is not helpful, nor is the information on kernel boot option statements.

Can anyone give me a suggestion or hint on how to get Ubuntu booted in this situation?

---

