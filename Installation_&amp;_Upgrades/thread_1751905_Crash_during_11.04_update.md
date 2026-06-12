---
title: "Crash during 11.04 update"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by LifeTec88 on 2011-05-07
Dear all,

I was updating my netbook to the 11.04 when it crashed (I thought is was on the grid, what do you think? it wasn't!) Now if I try to do it again I get a  notification and then it stops.
These are the last few lines of/var/log/dist-upgrade/main.log:

2011-05-07 11:15:47,352 DEBUG entry 'deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository' is already set to new dist
2011-05-07 11:15:47,353 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner'
2011-05-07 11:15:47,353 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner' is already set to new dist
2011-05-07 11:15:47,354 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main'
2011-05-07 11:15:47,355 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main' updated to new dist
2011-05-07 11:15:47,405 DEBUG running doUpdate() (showErrors=True)
2011-05-07 11:15:48,260 DEBUG openCache()
2011-05-07 11:15:48,261 DEBUG failed to SystemUnLock() (E:Niet vergrendeld) 
2011-05-07 11:15:48,620 DEBUG /openCache(), new cache size 1668
2011-05-07 11:15:48,622 DEBUG needServerMode(): run in 'desktop' mode, (because of key deps for 'ubuntu-desktop')
2011-05-07 11:15:48,623 ERROR No 'ubuntu-minimal' available/downloadable after sources.list rewrite+update
2011-05-07 11:16:13,016 DEBUG abort called
2011-05-07 11:16:13,027 DEBUG openCache()
2011-05-07 11:16:13,028 DEBUG failed to SystemUnLock() (E:Niet vergrendeld) 
2011-05-07 11:16:13,440 DEBUG /openCache(), new cache size 1668
2011-05-07 11:16:13,442 DEBUG enabling apt cron job

Do you guys know what to do? It's probably something small but I don't have a clue at the moment.

---

### Post by linuxftw3 on 2011-05-07
> **LifeTec88 said:**
> Dear all,

I was updating my netbook to the 11.04 when it crashed (I thought is was on the grid, what do you think? it wasn't!) Now if I try to do it again I get a  notification and then it stops.
These are the last few lines of/var/log/dist-upgrade/main.log:

2011-05-07 11:15:47,352 DEBUG entry 'deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository' is already set to new dist
2011-05-07 11:15:47,353 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner'
2011-05-07 11:15:47,353 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner' is already set to new dist
2011-05-07 11:15:47,354 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main'
2011-05-07 11:15:47,355 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main' updated to new dist
2011-05-07 11:15:47,405 DEBUG running doUpdate() (showErrors=True)
2011-05-07 11:15:48,260 DEBUG openCache()
2011-05-07 11:15:48,261 DEBUG failed to SystemUnLock() (E:Niet vergrendeld) 
2011-05-07 11:15:48,620 DEBUG /openCache(), new cache size 1668
2011-05-07 11:15:48,622 DEBUG needServerMode(): run in 'desktop' mode, (because of key deps for 'ubuntu-desktop')
2011-05-07 11:15:48,623 ERROR No 'ubuntu-minimal' available/downloadable after sources.list rewrite+update
2011-05-07 11:16:13,016 DEBUG abort called
2011-05-07 11:16:13,027 DEBUG openCache()
2011-05-07 11:16:13,028 DEBUG failed to SystemUnLock() (E:Niet vergrendeld) 
2011-05-07 11:16:13,440 DEBUG /openCache(), new cache size 1668
2011-05-07 11:16:13,442 DEBUG enabling apt cron job

Do you guys know what to do? It's probably something small but I don't have a clue at the moment.


downgrade to Maverick Meerkat, that should solve your problem.

---

### Post by dino99 on 2011-05-07
2011-05-07 11:15:48,261 DEBUG failed to SystemUnLock() (E:Niet vergrendeld) 

that mean than either a screensaver or a suspend/hibernate setting have disturb your upgrade

 (ALWAYS stop process/cronjob before such main change, and be carefull if using battery indeed)

now:

boot on recovery mode and select "repair package"
( hold "shift" key down at bios end process to get the grub menu)

---

