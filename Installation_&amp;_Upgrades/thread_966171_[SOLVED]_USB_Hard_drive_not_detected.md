---
title: "[SOLVED] USB Hard drive not detected"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by evanb on 2008-11-01
On at least two occasions I have plugged my portable USB drive into my Ubuntu system and it has utterly failed to detect the drive. Not only didn't the drive auto-mount, the filesystem (e.g., /dev/disks/by-id) showed no sign of it. Cycling power on my external hub, plugging the drive into the computer directly, even rebooting (although without powering off) did not restore access to the drive.

The solution? Run lsusb. The mere act of running the program caused the lights on my external hub to flash and the drive to miraculously appear on its usual mount point. I haven't seen anyone else relate a similar story, but here it is as another data point for people with USB problems.

If anyone else has had the same experience please post a reply. I'm curious if we might have some hardware or software in common that could be blamed for this behavior.

-eb-

---

