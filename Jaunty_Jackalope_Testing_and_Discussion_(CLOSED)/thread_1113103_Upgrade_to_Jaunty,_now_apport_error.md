---
title: "Upgrade to Jaunty, now apport error"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sjprice on 2009-04-01
Upgraded to Jaunty, and a few things not working as expected, no big deal, its beta.

But whenever I try and install/add/remove programs via update manager/apt-get, appport wants to upgrade to 0.147, and the upgrade fails with:
```
E: /var/cache/apt/archives/apport_0.147_all.deb: subprocess new pre-removal script returned error exit status 2
```

details:
```
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 166592 files and directories currently installed.)
Preparing to replace apport 0.146 (using .../archives/apport_0.147_all.deb) ...
 * Stopping automatic crash report generation: apport
/etc/init.d/apport: 24: runlevel: not found
exit: 24: Illegal number: Stopping
invoke-rc.d: initscript apport, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
 * Stopping automatic crash report generation: apport
/etc/init.d/apport: 24: runlevel: not found
exit: 24: Illegal number: Stopping
invoke-rc.d: initscript apport, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/apport_0.147_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
 * Starting automatic crash report generation: apport
/etc/init.d/apport: 24: runlevel: not found
exit: 24: Illegal number: Starting
invoke-rc.d: initscript apport, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2

```

Is there a way to get around it?

Thanks.

Update:

So went through Synaptic and tried to remove apport entirely and got
```
E: apport: Package is in a very bad inconsistent state - you should 
```

No, it didnt forget to copy the whole text, it stopped saying what I should do. :) Of course in the details of the terminal it said I should reinstall before removing, but I dont have the option to reinstall.

---

### Post by sjprice on 2009-04-01
Bump for the evening crowd.

---

### Post by sjprice on 2009-04-02
Bump for the morning crowd. Also noticed that Apport is now .148, same errors though.

```
E: /var/cache/apt/archives/apport_0.148_all.deb: subprocess new pre-removal script returned error exit status 2
```

```
(Reading database ... 167154 files and directories currently installed.)
Preparing to replace apport 0.146 (using .../archives/apport_0.148_all.deb) ...
 * Stopping automatic crash report generation: apport
/etc/init.d/apport: 24: runlevel: not found
exit: 24: Illegal number: Stopping
invoke-rc.d: initscript apport, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
 * Stopping automatic crash report generation: apport
/etc/init.d/apport: 24: runlevel: not found
exit: 24: Illegal number: Stopping
invoke-rc.d: initscript apport, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/apport_0.148_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
 * Starting automatic crash report generation: apport
/etc/init.d/apport: 24: runlevel: not found
exit: 24: Illegal number: Starting
invoke-rc.d: initscript apport, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/apport_0.148_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing apport (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 apport


```

Thoughts?

---

