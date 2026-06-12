---
title: "Update tzdata sets server to UTC"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by edgreenberg on 2011-05-03
I operate a farm of 40 or so Ubuntu servers. Mostly Hardy, some Lucid. 

Last week, we did safe-upgrade across the farm, and discovered that almost all of our servers had slipped to UTC along with the upgrade of TZDATA. 

The /etc/localtime file still was correct for the zone that was present previously, but typing date reported in UTC, and the syslog daemon was logging in UTC. 

A reboot fixed the problem, but rebooting customer servers seems suboptimal. 


From the safe-upgrade run:
Preparing to replace tzdata 2011e~repack-0ubuntu0.8.04 (using .../tzdata_2011g~repack-0ubuntu0.8.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2011g~repack-0ubuntu0.8.04) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline

Current default timezone: 'America/New_York'
Local time is now:      Tue May  3 10:08:58 EDT 2011.
Universal Time is now:  Tue May  3 14:08:58 UTC 2011.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

After doing this, date reported in UTC. 

Can anybody tell me what's going on, and how to resolve it without a reboot? 


Thanks,

Ed G

---

