---
title: "Delay before login"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by Decline- on 2007-11-05
All since I installed Ubuntu 7.10 (fresh system install, but with home partition from 7.04), there has been a delay between the boot screen and the login UI. Took about a minute or two. It's just a black screen with a blinking cursor on it, and neither CTRL+ALT+DEL, CTRL+ALT+BACKSPACE, CTRL+Z/C, CTRL+ALT+F1 or anything similar works. I just have to wait until X starts and the login screen appears.

This time, after using my Win XP partition for a while, it actually took like 5 minutes until I was able to log in! That's TOO much! So any help would be very much appreciated.

This is from /var/log/kern.log:
[I]
Nov  6 02:12:35 decline-laptop kernel: [   12.820000] intel_rng: FWH not detected
Nov  6 02:12:35 decline-laptop kernel: [   13.512000] lp: driver loaded but no devices found
Nov  6 02:12:35 decline-laptop kernel: [   13.560000] Adding 2931852k swap on /dev/sda3.  Priority:-1 extents:1 across:2931852k
Nov  6 02:12:35 decline-laptop kernel: [   14.576000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Nov  6 02:12:35 decline-laptop kernel: [   81.548000] EXT3 FS on sda1, internal journal
Nov  6 02:12:35 decline-laptop kernel: [  300.080000] kjournald starting.  Commit interval 5 seconds
Nov  6 02:12:35 decline-laptop kernel: [  300.080000] EXT3 FS on sda2, internal journal
Nov  6 02:12:35 decline-laptop kernel: [  300.080000] EXT3-fs: mounted filesystem with ordered data mode.
Nov  6 02:12:35 decline-laptop kernel: [  302.492000] ACPI: AC Adapter [AC] (on-line)[/I]

From /var/log/messages:
[i]Nov  6 02:12:35 decline-laptop kernel: [   13.560000] Adding 2931852k swap on /dev/sda3.  Priority:-1 extents:1 across:2931852k
Nov  6 02:12:35 decline-laptop kernel: [   14.576000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Nov  6 02:12:35 decline-laptop kernel: [   81.548000] EXT3 FS on sda1, internal journal
Nov  6 02:12:35 decline-laptop kernel: [  300.080000] kjournald starting.  Commit interval 5 seconds
Nov  6 02:12:35 decline-laptop kernel: [  300.080000] EXT3 FS on sda2, internal journal
Nov  6 02:12:35 decline-laptop kernel: [  300.080000] EXT3-fs: mounted filesystem with ordered data mode.[/i]

Can't seem to find anything of interest in Xorg.0.log.....

Usplash seems to be working fine when launching it etc...

Thanks.

---

### Post by Decline- on 2007-11-06
Might it have something to do with kjournald? I did some searching on it, but couldn't find anything useful..?

---

### Post by Decline- on 2007-11-06
Okay a quick "fix" for this is by disabling fsck for root and home partitions. Now the black screen only appears for a second or so. Dirty, but it works.

---

