---
title: "Ubuntu 16.04 no longer boots"
date: 2018-07-11
forum: Installation &amp; Upgrades
---

### Post by jahargreaves on 2018-07-11
I have a workstation that has Ubuntu 16.04 server installed on a pair of mirrored disks (software RAID 0), with Ubuntu desktop installed on top. When I last used it a few months ago it was working fine, though was producing warnings about the boot drive being full. Switching it on today it not longer boots - after the bios message you simply get a blank black screen. I have run the Boot Repair tool and it detects the raid (or at least it requires you to install mdadm and then doesn't issue any error messages) and claims to fix the boot sector, but it still won't boot. Holding shift doesn't make the GRUB menu appear either.

The pastebin is here: [http://paste.ubuntu.com/p/PW63N2Rb7Y/](http://paste.ubuntu.com/p/PW63N2Rb7Y/)

Any advice on how to proceed would be much appreciated, as I urgently need to run some jobs using this machine.

Many thanks, Jon

---

### Post by ajgreeny on 2018-07-11
From another live boot please show the output of ```
df -hT
``` which should tell us how much space you have on your system partitions, though my knowledge of RAID is just about zero, so I hope that command still gives useful info to us.

---

