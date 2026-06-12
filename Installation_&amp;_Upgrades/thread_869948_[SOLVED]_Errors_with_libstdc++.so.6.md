---
title: "[SOLVED] Errors with libstdc++.so.6"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by fowie on 2008-07-25
I'm running Ubuntu Dapper on my web server.  I've suddenly started getting an odd error.  I booted up one day to find I could not run certain programs.  Mysql failed to start, as did apache, and trying to run apt gave me this message:
```

apt-get: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```
GCC 4.2.0 is not available for Dapper in the repositories.  Looking into things a little further, I found that /usr/lib/libstdc++.so.6 was a symlink to /usr/lib/libstdc++.so.6.0.8, and I did have /usr/lib/libstdc++.so.6.0.7 available.  I changed the symlink to point to .6.0.7 and programs started working again.  However, I still have a recurrent problem with setting locates (not remedied by reinstalling locales package or any of the usual fixes) and apache processes are segfaulting on some of my web applications.  When I did an apt-get update it installed a new version of a few items include PHP and clamav, and reverted my symlink back to .6.0.8, causing things to again stop working.  Any help would be very appreciated.

---

### Post by fowie on 2008-09-16
Reinstalled Hardy from scratch to fix problem.

---

