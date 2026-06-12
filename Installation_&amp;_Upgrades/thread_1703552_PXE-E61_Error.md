---
title: "PXE-E61 Error"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by caddy400ex on 2011-03-09
Alright to start I am a linux n00b, now that we got that out of the way. I have ubuntu 10.10 installed on my laptop (HP pavilion zv6000). Everything worked fine for awhile. Then sometimes it started giving me a some /dev/0loop error on start up. If i rebooted it would then boot fine. I will admit the next part, which is my real issue is probably my fault. I wanted to uninstall ubuntu and do a fresh install of backtrack 4. I read some forums (not on here which probably was a mistake) and was told that I could run a live usb with ubuntu and open a terminal with some commands that would wipe my HDD. The command was something like **sudo shred -n2 -v** something similar to that. I ran the command on the 3 partitions that it said I had on the HDD. Everything ran fine then I restarted my laptop but with the USB that had the Backtrack 4 .ISO on it. When the laptop rebooted Unetbootin asked me what I wanted to boot. I chose default. The only thing that happend was a black screen and it said something about Ubuntu 10.10 on it. I rebooted and from then on my laptop will only goes to a black screen that gives me the PXE-E61 error and just keeps repeating itself. I have tried booting with the Ubuntu USB and Backtrack USB. I have nothing now. I know the HDD is connected properly because it was literally working 2 min before this error and the laptop was not bumped or anything. Could this be because of the shred command? If anybody could help me I would appreciate it.

---

### Post by caddy400ex on 2011-03-09
Ok so no help I guess.  I tried to run DBAN to nuke the drive but i get a *ERROR /dev/sdb (process crash) and the same thing for /dev/sda
 
 
Any other ideas?

---

