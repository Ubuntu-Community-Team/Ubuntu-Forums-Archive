---
title: "ubuntu-server via nano cpu freezes minute after boot restart"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by lemonjelo on 2011-05-05
I had the same problem awhile back on this system and couldn't find the solution this time around, but stumbled across it - I think it's the same issue and the aptitude upgrade last night brought it back: ondemand

The symptom is after a reboot and tailing logfiles and such, there's not indication why the system hangs up completely - it doesn't take long, more than a minute apparently.

Disabling the ondemand init script appears to be the fix.  Looking at /etc/init.d/ondemand it has a 60 second delay so that explains the delay.

I manually moved /etc/rc{2,3,4,5}.d/S99ondemand to K01ondemand - I also removed Default-Start: 2 3 4 5 from the preamble of /etc/init.d/ondemand and ran "update-rc.d ondemand default".  I suspect the recent upgrade "fixed" the old init script I had removed or changed or whatever.


I've attached a dmesg from the server.  also
cat /etc/debian_version 
squeeze/sid

uname -a
Linux lmno 2.6.32-31-server #61-Ubuntu SMP Fri Apr 8 19:44:42 UTC 2011 x86_64 GNU/Linux

---

### Post by Eeqmcsq on 2011-07-03
I just came across this exact same problem with my VIA Nano installation. Using your clue about the ondemand script, I ran some tests and got more information about of the problem.

I have filed [BUG#805205]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/805205") with my findings.

---

### Post by Eeqmcsq on 2013-02-09
I finally solved this hanging problem. I needed a BIOS update.

---

### Post by howefield on 2013-02-09
Old thread closed.

---

