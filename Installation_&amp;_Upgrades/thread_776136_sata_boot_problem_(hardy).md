---
title: "sata boot problem (hardy)"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Skylar626 on 2008-04-30
Linux Familiarity: Low

I have two hard drives, one with windows xp and one with ubuntu. I upgraded using the update manager to hardy lts. When it restarted after the lengthy upgrade process, grub prompt came up and displayed what I felt was the proper screen, showing both my 8.04 ubuntu and windows professional xp boot options. When I selected the 8.04 option it hung on the load screen for a really long time and then dropped me into:

```

BusyBox v1.1.3(Debian 1:1.1.3-Subuntu12) Built-in shell (ash)
(initramfs)
```

I restarted, this time in recovery mode and found that it was hanging on mounting ata1 which is the sata drive that linux is installed on:

```
...
ata1 Sata link up 3.0 Gbps SStatus123 Scontrol300
[pause for a while]
ata1.00 qc time out (cmd 0xec)
ata1.00 failed to IDENTIFY (I/O error err_mask=0x4)
ata failed to recover some devices, retrying in 5 seconds
```

it then retried about 4 times then proceeded with finding the keyboard and stuff then said:
```
Check root= bootarg cat /proc/cmdline or missing modules, devices: cat proc/modules ls /dev
ALERT! /dev/disk/by-uuid/512177f58-1018-44df-bce1-a1a7e7d5724c does not exist. Dropping to a shell!
BusyBox v1.1.3(Debian 1:1.1.3-Subuntu12) Built-in shell (ash)
(initramfs)
```

I don't really even know where to proceed from here. I don't have a live cd but if that is what is necessary then i can obtain one. I will be away until about 9pm cst and will follow whomever gives me reasonable direction to the letter at that time :)

---

