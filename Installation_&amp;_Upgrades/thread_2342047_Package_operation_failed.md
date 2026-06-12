---
title: "Package operation failed"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by kanishka7878 on 2016-11-03
The installation or removal of a software package failed.

whenever I try to install this update it shows package operation failed, the details of the update are in screen shot.

---

### Post by howefield on 2016-11-03
Close the update manager and try it from the terminal..

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Then post back the errors, if indeed there are any.

---

### Post by kanishka7878 on 2016-11-03
it shows this after upgrade, but no change

After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 561955 files and directories currently installed.)
Preparing to unpack .../power-commands_0.2.0-0extras14.04.0_all.deb ...
Unpacking power-commands (0.2.0-0extras14.04.0) over (0.1.7-0extras14.04.0) ...
dpkg: error processing archive /var/cache/apt/archives/power-commands_0.2.0-0extras14.04.0_all.deb (--unpack):
 trying to overwrite '/usr/share/applications/shutdown.desktop', which is also in package session-shortcuts 1.2
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/power-commands_0.2.0-0extras14.04.0_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

