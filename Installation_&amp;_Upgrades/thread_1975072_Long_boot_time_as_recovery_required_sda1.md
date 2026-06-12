---
title: "Long boot time as recovery required sda1"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by owise1 on 2012-05-06
Have just done a sequence of updates from 10.10 to 12.04 on this eeepC 1005HA.  Runs well and upgrade was smooth.  Only problem I have now is the slow startup due to what appears to be a need to do a recovery on sda1 at every re-boot - see dmesg output below.  Any ideas??

Dave


[    3.250025] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.250034] EXT4-fs (sda1): write access will be enabled during recovery
[    3.627485] sd 6:0:0:0: [sdb] 3970048 512-byte logical blocks: (2.03 GB/1.89 GiB)
[    3.628352] sd 6:0:0:0: [sdb] Write Protect is off
[    3.628363] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    3.629235] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.629243] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.633454] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.633463] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.634707]  sdb: sdb1
[    3.640838] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.640849] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.640857] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   16.218820] EXT4-fs (sda1): recovery complete
[   16.221415] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   35.369693] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by jadtech on 2012-05-06
i have an Idea :) 

if you are on a dual boot machine  boot up windows do a defrag of the  and a chkdisk whole Hard drive  or get defrag for linux my bet is after all that  the Hard drive needs a little clean up ..

there is a good chance  the drive could have a few bad spots

---

### Post by owise1 on 2012-05-06
Thanks for the suggestion but this is not a dual boot machine - installed linux from new without ever booting into XP!

---

### Post by jadtech on 2012-05-06
good deal you can still do the check and there is a program  for defraging linux though many say its not nessary there are them times it  does ..

---

### Post by ravisghosh on 2012-06-23
Got the same problem on Dell 1555. Eagerly awaiting a fix for it.

---

### Post by nipunshakya on 2012-06-23
I think you can boot into LiveCD, run gparted  there, unmount the drives(if any mounted), and then right click on each drive, select 'check ' from the drop-down menu and apply the changes. This might help it out.

---

