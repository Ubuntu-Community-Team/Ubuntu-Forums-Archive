---
title: "[SOLVED] RAID checkarray kills my system - dead !"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2008-04-07
So, I've tied down one cause of my system hanging 'randomly'. However it's not ramdom as it happens, it dies on the first Sunday of every month which I've established is due to a cron script in /etc/cron.d/mdadm that runs a script called /usr/share/mdadm/checkarray. This script appears to do a parity check on my RAID 1 array, but after 10.1% the system hangs. This equates to approx. 5232768 blocks out of 51199040.

I've run it manually many times to try different settings, and it always hangs, and always at 10.1% or 10.2% complete on the first device /dev/md0.

I've tried it with the max bandwidth reduced to 10Mb/s (in /proc/sys/dev/raid/speed_limit_max), which had zero effect, other than the check ran more slowly as I would expect. I've also killed the process that runs mdadm --monitor, and ran the check on /dev/md2 with bandwidt reset to the default 200Mb/s. This was more successful, as it got to 20.8% through a much larger drive (49886016 blocks out of 239737856). The end result was exactly the same unfortunately. I noticed that the max bandwidth consumed never rose above 13Mb/s, which I guess is the limit of my system hardware.

I'm running Gutsy (2.6.22-14-server) on a a (don't laugh !) Pentium III 500MHz dual-CPU with 1Gb
RAM, 2x300Gb Seagate Barracuda ATA (IDE) disks.

I don't know what to try next - anyone got any other ideas ?

---

### Post by dbyrne on 2008-05-30
Not solved as such, but I upgraded the Tyan Tiger-100 motherboard, dual PIII 500MHz for an Asus P4S800D-E Deluxe motherboard, Pentium 4 3GHz and the problem does not occur. All arrays check out fine and the process runs to completion without crashing the system.

Go figure !

---

