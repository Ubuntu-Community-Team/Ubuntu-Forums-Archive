---
title: "How to roll back all updates done at one specific time ?"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2008-11-10
I tried to cancel an update of 70 files because the download was extreamlly slow (hours)  but instead it simply stop downloading all that it did not fetched and installed what it did get. So it may have installed partial packages.

How do I roll back all of what it installed just now ?  I do not have the list of what it installed.

Because of this I am afraid it is going to mess up my whole system with partial installs. I want to prevent this as much as possible because I have no backups !!!

Found a log of what it seams to have done at that time:
> />cat /var/log/dpkg.log
2008-11-10 00:13:51 startup archives unpack
2008-11-10 00:14:03 install linux-image-2.6.24-21-generic <none> 2.6.24-21.43
2008-11-10 00:14:03 status half-installed linux-image-2.6.24-21-generic 2.6.24-21.43
2008-11-10 00:14:19 status unpacked linux-image-2.6.24-21-generic 2.6.24-21.43
2008-11-10 00:14:19 status unpacked linux-image-2.6.24-21-generic 2.6.24-21.43
2008-11-10 00:14:20 install linux-ubuntu-modules-2.6.24-21-generic <none> 2.6.24-21.32
2008-11-10 00:14:20 status half-installed linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32
2008-11-10 00:14:26 status unpacked linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32
2008-11-10 00:14:26 status unpacked linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32
2008-11-10 00:14:26 upgrade libdbus-1-dev 1.1.20-1ubuntu2 1.1.20-1ubuntu3.1
2008-11-10 00:14:26 status half-configured libdbus-1-dev 1.1.20-1ubuntu2
2008-11-10 00:14:26 status unpacked libdbus-1-dev 1.1.20-1ubuntu2
2008-11-10 00:14:26 status half-installed libdbus-1-dev 1.1.20-1ubuntu2
2008-11-10 00:14:26 status half-installed libdbus-1-dev 1.1.20-1ubuntu2
2008-11-10 00:14:26 status unpacked libdbus-1-dev 1.1.20-1ubuntu3.1
2008-11-10 00:14:26 status unpacked libdbus-1-dev 1.1.20-1ubuntu3.1
2008-11-10 00:14:27 upgrade libdbus-1-3 1.1.20-1ubuntu2 1.1.20-1ubuntu3.1
2008-11-10 00:14:27 status half-configured libdbus-1-3 1.1.20-1ubuntu2
2008-11-10 00:14:27 status unpacked libdbus-1-3 1.1.20-1ubuntu2
2008-11-10 00:14:27 status half-installed libdbus-1-3 1.1.20-1ubuntu2
2008-11-10 00:14:27 status half-installed libdbus-1-3 1.1.20-1ubuntu2
2008-11-10 00:14:27 status unpacked libdbus-1-3 1.1.20-1ubuntu3.1
2008-11-10 00:14:27 status unpacked libdbus-1-3 1.1.20-1ubuntu3.1
2008-11-10 00:14:27 upgrade cupsys-common 1.3.7-1ubuntu3 1.3.7-1ubuntu3.1
2008-11-10 00:14:27 status half-configured cupsys-common 1.3.7-1ubuntu3
2008-11-10 00:14:27 status unpacked cupsys-common 1.3.7-1ubuntu3
2008-11-10 00:14:27 status half-installed cupsys-common 1.3.7-1ubuntu3
2008-11-10 00:14:27 status half-installed cupsys-common 1.3.7-1ubuntu3
2008-11-10 00:14:27 status unpacked cupsys-common 1.3.7-1ubuntu3.1
2008-11-10 00:14:27 status unpacked cupsys-common 1.3.7-1ubuntu3.1
2008-11-10 00:14:28 upgrade libcupsys2 1.3.7-1ubuntu3 1.3.7-1ubuntu3.1
2008-11-10 00:14:28 status half-configured libcupsys2 1.3.7-1ubuntu3
2008-11-10 00:14:28 status unpacked libcupsys2 1.3.7-1ubuntu3
2008-11-10 00:14:28 status half-installed libcupsys2 1.3.7-1ubuntu3
2008-11-10 00:14:28 status half-installed libcupsys2 1.3.7-1ubuntu3
2008-11-10 00:14:28 status unpacked libcupsys2 1.3.7-1ubuntu3.1
2008-11-10 00:14:28 status unpacked libcupsys2 1.3.7-1ubuntu3.1
2008-11-10 00:14:28 upgrade libcupsimage2 1.3.7-1ubuntu3 1.3.7-1ubuntu3.1
2008-11-10 00:14:28 status half-configured libcupsimage2 1.3.7-1ubuntu3
2008-11-10 00:14:28 status unpacked libcupsimage2 1.3.7-1ubuntu3
2008-11-10 00:14:28 status half-installed libcupsimage2 1.3.7-1ubuntu3
2008-11-10 00:14:28 status half-installed libcupsimage2 1.3.7-1ubuntu3
2008-11-10 00:14:28 status unpacked libcupsimage2 1.3.7-1ubuntu3.1
2008-11-10 00:14:28 status unpacked libcupsimage2 1.3.7-1ubuntu3.1
2008-11-10 00:14:28 upgrade cupsys 1.3.7-1ubuntu3 1.3.7-1ubuntu3.1
2008-11-10 00:14:28 status half-configured cupsys 1.3.7-1ubuntu3
2008-11-10 00:14:29 status unpacked cupsys 1.3.7-1ubuntu3
2008-11-10 00:14:29 status half-installed cupsys 1.3.7-1ubuntu3
2008-11-10 00:14:30 status half-installed cupsys 1.3.7-1ubuntu3
2008-11-10 00:14:30 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:14:30 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:14:31 upgrade cupsys-bsd 1.3.7-1ubuntu3 1.3.7-1ubuntu3.1
2008-11-10 00:14:31 status half-configured cupsys-bsd 1.3.7-1ubuntu3
2008-11-10 00:14:32 status unpacked cupsys-bsd 1.3.7-1ubuntu3
2008-11-10 00:14:32 status half-installed cupsys-bsd 1.3.7-1ubuntu3
2008-11-10 00:14:32 status half-installed cupsys-bsd 1.3.7-1ubuntu3
2008-11-10 00:14:32 status unpacked cupsys-bsd 1.3.7-1ubuntu3.1
2008-11-10 00:14:32 status unpacked cupsys-bsd 1.3.7-1ubuntu3.1
2008-11-10 00:14:32 upgrade cupsys-client 1.3.7-1ubuntu3 1.3.7-1ubuntu3.1
2008-11-10 00:14:32 status half-configured cupsys-client 1.3.7-1ubuntu3
2008-11-10 00:14:32 status unpacked cupsys-client 1.3.7-1ubuntu3
2008-11-10 00:14:32 status half-installed cupsys-client 1.3.7-1ubuntu3
2008-11-10 00:14:32 status half-installed cupsys-client 1.3.7-1ubuntu3
2008-11-10 00:14:32 status unpacked cupsys-client 1.3.7-1ubuntu3.1
2008-11-10 00:14:32 status unpacked cupsys-client 1.3.7-1ubuntu3.1
2008-11-10 00:14:33 upgrade dbus 1.1.20-1ubuntu2 1.1.20-1ubuntu3.1
2008-11-10 00:14:33 status half-configured dbus 1.1.20-1ubuntu2
2008-11-10 00:14:33 status unpacked dbus 1.1.20-1ubuntu2
2008-11-10 00:14:33 status half-installed dbus 1.1.20-1ubuntu2
2008-11-10 00:14:33 status half-installed dbus 1.1.20-1ubuntu2
2008-11-10 00:14:33 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-10 00:14:33 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-10 00:14:33 upgrade dbus-x11 1.1.20-1ubuntu2 1.1.20-1ubuntu3.1
2008-11-10 00:14:33 status half-configured dbus-x11 1.1.20-1ubuntu2
2008-11-10 00:14:33 status unpacked dbus-x11 1.1.20-1ubuntu2
2008-11-10 00:14:33 status half-installed dbus-x11 1.1.20-1ubuntu2
2008-11-10 00:14:33 status half-installed dbus-x11 1.1.20-1ubuntu2
2008-11-10 00:14:33 status unpacked dbus-x11 1.1.20-1ubuntu3.1
2008-11-10 00:14:33 status unpacked dbus-x11 1.1.20-1ubuntu3.1
2008-11-10 00:14:34 startup packages configure
2008-11-10 00:14:34 configure linux-image-2.6.24-21-generic 2.6.24-21.43 2.6.24-21.43
2008-11-10 00:14:34 status unpacked linux-image-2.6.24-21-generic 2.6.24-21.43
2008-11-10 00:14:34 status half-configured linux-image-2.6.24-21-generic 2.6.24-21.43
2008-11-10 00:15:14 status installed linux-image-2.6.24-21-generic 2.6.24-21.43
2008-11-10 00:15:14 configure linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32 2.6.24-21.32
2008-11-10 00:15:14 status unpacked linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32
2008-11-10 00:15:14 status half-configured linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32
2008-11-10 00:15:32 status installed linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32
2008-11-10 00:15:32 configure libdbus-1-3 1.1.20-1ubuntu3.1 1.1.20-1ubuntu3.1
2008-11-10 00:15:32 status unpacked libdbus-1-3 1.1.20-1ubuntu3.1
2008-11-10 00:15:32 status half-configured libdbus-1-3 1.1.20-1ubuntu3.1
2008-11-10 00:15:32 status installed libdbus-1-3 1.1.20-1ubuntu3.1
2008-11-10 00:15:32 status triggers-pending libc6 2.7-10ubuntu4
2008-11-10 00:15:32 configure libdbus-1-dev 1.1.20-1ubuntu3.1 1.1.20-1ubuntu3.1
2008-11-10 00:15:32 status unpacked libdbus-1-dev 1.1.20-1ubuntu3.1
2008-11-10 00:15:32 status half-configured libdbus-1-dev 1.1.20-1ubuntu3.1
2008-11-10 00:15:32 status installed libdbus-1-dev 1.1.20-1ubuntu3.1
2008-11-10 00:15:32 configure cupsys-common 1.3.7-1ubuntu3.1 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys-common 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status half-configured cupsys-common 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status installed cupsys-common 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 configure libcupsys2 1.3.7-1ubuntu3.1 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked libcupsys2 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status half-configured libcupsys2 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status installed libcupsys2 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 configure libcupsimage2 1.3.7-1ubuntu3.1 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked libcupsimage2 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status half-configured libcupsimage2 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status installed libcupsimage2 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 configure cupsys 1.3.7-1ubuntu3.1 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status unpacked cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:32 status half-configured cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:37 status installed cupsys 1.3.7-1ubuntu3.1
2008-11-10 00:15:37 configure cupsys-client 1.3.7-1ubuntu3.1 1.3.7-1ubuntu3.1
2008-11-10 00:15:37 status unpacked cupsys-client 1.3.7-1ubuntu3.1
2008-11-10 00:15:37 status half-configured cupsys-client 1.3.7-1ubuntu3.1
2008-11-10 00:15:37 status installed cupsys-client 1.3.7-1ubuntu3.1
2008-11-10 00:15:37 configure cupsys-bsd 1.3.7-1ubuntu3.1 1.3.7-1ubuntu3.1
2008-11-10 00:15:37 status unpacked cupsys-bsd 1.3.7-1ubuntu3.1
2008-11-10 00:15:37 status half-configured cupsys-bsd 1.3.7-1ubuntu3.1
2008-11-10 00:15:38 status installed cupsys-bsd 1.3.7-1ubuntu3.1
2008-11-10 00:15:38 configure dbus 1.1.20-1ubuntu3.1 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status half-configured dbus 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status installed dbus 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 configure dbus-x11 1.1.20-1ubuntu3.1 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status unpacked dbus-x11 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status half-configured dbus-x11 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 status installed dbus-x11 1.1.20-1ubuntu3.1
2008-11-10 00:15:38 trigproc libc6 2.7-10ubuntu4 2.7-10ubuntu4
2008-11-10 00:15:38 status half-configured libc6 2.7-10ubuntu4
2008-11-10 00:15:38 status installed libc6 2.7-10ubuntu4


---

### Post by cariboo on 2008-11-10
You could try in a terminal:

```
sudo apt-get install -f
```

This should download the dependencies to fix the broken packages.

Jim

---

### Post by Browser_ice on 2008-11-10
In stopping the upgrade, I may have accidentally said YES in continue to ignore packages. If I did this, how do I make then un-ignored ?

---

