---
title: "Removing dansguardian messed up"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by mister harbies on 2007-09-09
Hi there,

I have removed dansguardian from my system, or so I think I have. It does not affect the running of my system so it is not obtrusive.

However, I get errors when I run synaptic or apt-get from terminal.

```

Setting up dansguardian (2.8.0.6-antivirus-6.4.4.1-2) ...
Starting DansGuardian: Error connecting to parent proxy
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error processing dansguardian (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dansguardian
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--remove):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: Error connecting to parent proxy
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dansguardian
```

I can still access the internet and the restricted sites so I know dansguardian is not functioning (or installed)

How can I completely remove dansguardian from the system? Just get rid of it. :)


Thank you,

---

### Post by mister harbies on 2007-09-15
Bump! Can anyone help me here?

---

