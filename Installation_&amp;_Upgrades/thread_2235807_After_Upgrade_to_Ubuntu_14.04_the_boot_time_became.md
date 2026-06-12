---
title: "After Upgrade to Ubuntu 14.04 the boot time became very long"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by vdeepakkumar on 2014-07-23
My Ubuntu 14.04 is dead slow during booting. After booting the KDE splash screen also takes several seconds to go away and to enter the desktop session. Please find the bootchart diagnostics below. Please help advise..

Bootchart is available here: [https://onedrive.live.com/redir?resid=3974EAB59564848E!3977&authkey=!AIJt3cmVBUINIsE&v=3&ithint=photo%2cpng](https://onedrive.live.com/redir?resid=3974EAB59564848E!3977&authkey=!AIJt3cmVBUINIsE&v=3&ithint=photo%2cpng)

---

### Post by oldfred on 2014-07-23
I never understood bootcharts and attached versions are usually too small anyway.

But look in dmseg for any timestamps with long differences. Not sure if one before or after is issue put that tells you where to start looking. No need to post entire dmseg.
You want to review errors, warnings, repeated tries at loading a driver and either sucess or failure and the long timestamp deltas.

If you can boot you should have a log file viewer. There are many other log files also.

If you cannot boot mount / partition from live installer:
 Change example sda6 to your Ubuntu partition
sudo mount /dev/sda6 /mnt
gksudo gedit /mnt/var/log/dmesg
or if you can boot to a terminal.
sudo nano /var/log/dmesg

---

