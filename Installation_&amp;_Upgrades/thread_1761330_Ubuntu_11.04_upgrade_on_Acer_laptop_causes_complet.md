---
title: "Ubuntu 11.04 upgrade on Acer laptop causes complete system hang within minutes"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by Khelair on 2011-05-18
After having had success on my primary desktop machine upgrading to Ubuntu 11.04 via the automated upgrade tool, I decided to bring my laptop up to speed, as well.  Both machines dual boot with Windows 7 and were previously running 10.10.

I got 11.04 on the laptop and was pleased to see the desktop appear after I booted for the first time and logged in.  I went to grab a cup of coffee and by the time I returned the HDD light was frozen on, the mouse pointer wouldn't move, keystrokes weren't recognized, and I couldn't switch to a text terminal.  I tried logging in from a different machine on my LAN and was also unable to get a prompt via ssh.

I tried several different methods of booting and it was always the same.  What really mystified me is that I got on and right away opened two remote windows with tail -f of /var/log/messages and /var/log/syslog and found nothing unusual before it reliably crashed within 3 minutes.

Finally I did some really in depth monitoring of what was going on in my system from the text console upon booting and found that *ubuntu one's syncd* was grabbing all of the available processor time for one core (this is a dual core amd athalon II) and spiking the load average to over 20 before the system became completely unresponsive.  I rebooted, killed the syncd before anything bogus happened, and my system has been stable since.  I do have to repeat this any time I reboot, however.

Not sure if this is the same bug that everybody else is having with system hangs upon boot of 11.04, but I wouldn't be surprised.  I'd be happy to forward logs or information to a bug report if somebody would tell me where to go for it.

Hope this helps out some others; more than anything I hope that it gets solved so that I don't have to kill -15 that syncd every time my system needs a reboot.  :|

TIA

---

### Post by eyedeal on 2011-05-26
FWIW, I've disabled Ubuntu One in the startup apps, and the system starts up faster, although I still have occasional hangs for unknown reasons.

---

