---
title: "Intermittent freeze on startup"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bcbc on 2010-04-03
I've had intermittent freezes on startup since Beta1 (I update daily). I removed 'quiet splash' to see where the problem was and this is what I got...
```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sdv1 has been mounted 35 times without being checked, check forced
/dev/sdb5: clean, 2301/655360 files, 126835/2620595 blocks
/dev/sdb1: 249551/524288 files (0.1% non-contiguous), 1300078/2096474 blocks
init: ureadahead-other main process (853) terminated with status 4
 * Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
								[ OK ]
 * Setting sensors limits					[ OK ] 
 * Starting Kernel Oops catching service kerneloops		[ OK ]
 [COLOR="DarkRed"]*[/COLOR] Speech-dispatcher configured for user sessions		
 * Startging Common Unix Printing System: cupsd			[ OK ]
 [COLOR="DarkRed"]*[/COLOR] PulseAudio configured for per-user sessions			
 * Enabling additional executable bunary formats binfmt-support	[ OK ]
 * Checking battery state...					     
```
The cursor sits over on the right of 'checking battery' and doesn't respond to any input.

Computer: dell inspiron 6400, T2400 1.83Ghz, ATI X1300, 1GB ram. The computer was running on AC, and the battery is operational and fully charged. I'm running Lucid off an external USB (Maxtor 100GB). I haven't had any issues running karmic (off internal HDD)

---

### Post by bcbc on 2010-04-05
It died in a different place this time - while it was checking the usb drive:

```
irect-Access Maxtor OneTouch II 023g PQ
ttached scsi generic sg2 type 0
sdb] 195813072 512-byte logical blocks: (100 GB/93.3
sdb] Write protect is off
sdb] Assuming drive through cache: write through
sdb] Assuming drive through cache: write through
```
It froze after that, the screen was corrupted. After reboot, the next line after the above said it was checking was the partitions on sdb.

Is anyone else booting lucid from an external usb having problems like the above?

---

