---
title: "server 13.10 fresh install with RAID 10 won't boot"
date: 2014-04-09
forum: Installation &amp; Upgrades
---

### Post by Kenny_Flynn on 2014-04-09
I am attempted to build my very first RAID using four, 3TB drives. After successfully completing the installation, I am unable to boot the fresh installation. Overall, the process has been a fun learning experience but I seem to be at the limit of what I can stumble through on my own using Google. 

```
error: disk 'mduuid/#' not found.
```

I used GParted to create three partitions on each of the four drives: an unformatted 1MB partition with the grub_bios flag, a 8000 MB swap partition and a third ext4 partition to take up the remaining space. Using [these instructions as a guide]("https://help.ubuntu.com/10.04/serverguide/advanced-installation.html#raid-degraded"), I configured md0 for the swap partitions and md1 for the large filesystem.

I have tried running the Boot-Repair-Disk but I have not been able to automatically repair the issue. [http://paste.ubuntu.com/7228596/](http://paste.ubuntu.com/7228596/)

As far as I can tell from mdadm output, the raid itself seems to be functioning correctly. All the drives seem to be active and healthy so I suspect the issue may lie in something I am missing with grub or with my DFI LanParty mobo.

I would appreciate any insight in what I could try next or what could be wrong. Thank you for your time.

---

