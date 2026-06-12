---
title: "do-release-upgrade &quot;Please install all available updates...&quot;"
date: 2023-05-08
forum: Installation &amp; Upgrades
---

### Post by dwater on 2023-05-08
I'm trying to upgrade 22.10/kinetic from the command line, but it keeps saying:

```
$ sudo do-release-upgrade Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

```

Searching online had me do various apt commands, as well as disable some files in /etc/apt/sources.list.d, but to no avail.

IINM, this might be indicating a cause, but I tried upgrading them, again, it didn't upgrade anything and so didn't help:

```
$ sudo apt list --upgradable -aListing... Done
libnautilus-extension4/kinetic-updates 1:43.2-0ubuntu1 amd64 [upgradable from: 1:43.0-1ubuntu2.1]
libnautilus-extension4/kinetic-security,now 1:43.0-1ubuntu2.1 amd64 [installed,upgradable to: 1:43.2-0ubuntu1]
libnautilus-extension4/kinetic 1:43.0-1ubuntu1 amd64


libnss-systemd/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
libnss-systemd/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
libnss-systemd/kinetic 251.4-1ubuntu7 amd64


libpam-systemd/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
libpam-systemd/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
libpam-systemd/kinetic 251.4-1ubuntu7 amd64


libsystemd-shared/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
libsystemd-shared/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
libsystemd-shared/kinetic 251.4-1ubuntu7 amd64


libsystemd0/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
libsystemd0/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
libsystemd0/kinetic 251.4-1ubuntu7 amd64


libsystemd0/kinetic-updates 251.4-1ubuntu7.3 i386 [upgradable from: 251.4-1ubuntu7.1]
libsystemd0/kinetic-security,now 251.4-1ubuntu7.1 i386 [installed,upgradable to: 251.4-1ubuntu7.3]
libsystemd0/kinetic 251.4-1ubuntu7 i386


libudev1/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
libudev1/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
libudev1/kinetic 251.4-1ubuntu7 amd64


libudev1/kinetic-updates 251.4-1ubuntu7.3 i386 [upgradable from: 251.4-1ubuntu7.1]
libudev1/kinetic-security,now 251.4-1ubuntu7.1 i386 [installed,upgradable to: 251.4-1ubuntu7.3]
libudev1/kinetic 251.4-1ubuntu7 i386


lldb/kinetic 1:15.0-55.1ubuntu1 amd64 [upgradable from: 1:14.0-55~exp2]
lldb/now 1:14.0-55~exp2 amd64 [installed,upgradable to: 1:15.0-55.1ubuntu1]


nautilus-data/kinetic-updates,kinetic-updates 1:43.2-0ubuntu1 all [upgradable from: 1:43.0-1ubuntu2.1]
nautilus-data/kinetic-security,kinetic-security,now 1:43.0-1ubuntu2.1 all [installed,upgradable to: 1:43.2-0ubuntu1]
nautilus-data/kinetic,kinetic 1:43.0-1ubuntu1 all


nautilus/kinetic-updates 1:43.2-0ubuntu1 amd64 [upgradable from: 1:43.0-1ubuntu2.1]
nautilus/kinetic-security,now 1:43.0-1ubuntu2.1 amd64 [installed,upgradable to: 1:43.2-0ubuntu1]
nautilus/kinetic 1:43.0-1ubuntu1 amd64


systemd-oomd/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
systemd-oomd/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
systemd-oomd/kinetic 251.4-1ubuntu7 amd64


systemd-resolved/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
systemd-resolved/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
systemd-resolved/kinetic 251.4-1ubuntu7 amd64


systemd-sysv/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
systemd-sysv/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
systemd-sysv/kinetic 251.4-1ubuntu7 amd64


systemd-timesyncd/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
systemd-timesyncd/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
systemd-timesyncd/kinetic 251.4-1ubuntu7 amd64


systemd/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
systemd/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
systemd/kinetic 251.4-1ubuntu7 amd64


udev/kinetic-updates 251.4-1ubuntu7.3 amd64 [upgradable from: 251.4-1ubuntu7.1]
udev/kinetic-security,now 251.4-1ubuntu7.1 amd64 [installed,upgradable to: 251.4-1ubuntu7.3]
udev/kinetic 251.4-1ubuntu7 amd64



```

```

sudo apt upgrade libnautilus-extension4 libnss-systemd libpam-systemd libsystemd0 libsystemd-shared libudev1 lldb nautilus nautilus-data systemd systemd-oomd systemd-resolved systemd-sysv systemd-timesyncd udev
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libsystemd0 : Breaks: libsystemd0:i386 (!= 251.4-1ubuntu7.3) but 251.4-1ubuntu7.1 is to be installed
 libsystemd0:i386 : Breaks: libsystemd0 (!= 251.4-1ubuntu7.1) but 251.4-1ubuntu7.3 is to be installed
 libudev1 : Breaks: libudev1:i386 (!= 251.4-1ubuntu7.3) but 251.4-1ubuntu7.1 is to be installed
 libudev1:i386 : Breaks: libudev1 (!= 251.4-1ubuntu7.1) but 251.4-1ubuntu7.3 is to be installed
 lldb-14 : Depends: python3-lldb-14 but it is not installable
E: Broken packages

```

Any ideas how to fix this?

---

### Post by TheFu on 2023-05-08
```
sudo apt update
sudo apt full-upgrade
sudo do-release-upgrade
```

If there is any error along the way, STOP. Don't do the next command(s).  Solve the first issue.

Before doing any release upgrade, you'll want a 100% know-you-can-restore backup made.  Thinks often go badly, after all, the release upgrade process is like replacing the engine and transmission for your car. It is a big deal. Bad things happen sometimes.  If you've done more than 2 release-upgrades to the same install already, it is time for a fresh install to clean out the cruft.

---

### Post by oldos2er on 2023-05-08
Just a note, if you've never run apt full-upgrade or its equivalent apt-get dist-upgrade, you will need to reboot before continuing with do-release-upgrade.

---

### Post by TheFu on 2023-05-08
> **oldos2er said:**
> Just a note, if you've never run apt full-upgrade or its equivalent apt-get dist-upgrade, you will need to reboot before continuing with do-release-upgrade.
+10 Definitely!  Thanks for that missing info.

---

### Post by dwater on 2023-05-08
> **TheFu said:**
> you'll want a 100% know-you-can-restore backup made. 

Any pointers on how to do this?

I have timeshift going, but I suspect that won't restore *everything*. I had an external drive with enough empty space for the whole of my internal drive...what would you recommend?

---

### Post by TheFu on 2023-05-09
> **dwater said:**
> Any pointers on how to do this?

I have timeshift going, but I suspect that won't restore *everything*. I had an external drive with enough empty space for the whole of my internal drive...what would you recommend?

I've posted backup methods and restore techniques to these forums 100+ times.  Read.

---

