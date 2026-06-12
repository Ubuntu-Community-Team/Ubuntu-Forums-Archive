---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-11-15
forum: Installation &amp; Upgrades
---

### Post by fathomstory on 2017-11-15
Greetings, 

I am running: 4.10.0-38-lowlatency #42-Ubuntu x86_64 x86_64 GNU/Linux Ubuntu 17.04

I used the GUI to update my system and it crashed. I then went to command line and get this:

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up drbdlinks (1.22-1) ...
Job for drbdlinksclean.service canceled.
invoke-rc.d: initscript drbdlinksclean, action "start" failed.
&#9679; drbdlinksclean.service - LSB: Clean up drbdlinks links on system boot or shutdown.
   Loaded: loaded (/etc/init.d/drbdlinksclean; generated; vendor preset: enabled)
   Active: inactive (dead) since Wed 2017-11-15 15:58:09 EST; 7ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 8817 ExecStart=/etc/init.d/drbdlinksclean start (code=killed, signal=TERM)
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/drbdlinksclean.service

Nov 15 15:58:09 datacide systemd[1]: Starting LSB: Clean up drbdlinks links on system boot or shutdown....
Nov 15 15:58:09 datacide systemd[1]: Stopped LSB: Clean up drbdlinks links on system boot or shutdown..
Nov 15 15:58:09 datacide drbdlinksclean[8817]: Stopping drbdlinksclean (via systemctl): drbdlinksclean.service.
dpkg: error processing package drbdlinks (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 drbdlinks
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

-----------------

I rebooted several times, I purged and reinstalled drbdlinks, I tried different methods of autoremove, clean and such. I still get these messages. How to rectify?

---

