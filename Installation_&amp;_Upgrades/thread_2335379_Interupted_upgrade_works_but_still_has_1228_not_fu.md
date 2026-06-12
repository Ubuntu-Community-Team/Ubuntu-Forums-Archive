---
title: "Interupted upgrade works but still has: 1228 not fully installed or removed"
date: 2016-08-28
forum: Installation &amp; Upgrades
---

### Post by reg-dodds on 2016-08-28
After upgrading 14.04 LTS to 16.04 LTS the following message is given after executing 

```
apt-get update && apt-get upgrade 
. . . many lines omitted
Errors were encountered while processing:
 cron
 initscripts
 procps
 udev
 initramfs-tools-core
 initramfs-tools
 brltty
 bluez
 plymouth
 plymouth-theme-ubuntu-text
 plymouth-theme-kubuntu-text
 plymouth-label
 plymouth-theme-kubuntu-logo
 mountall
 upstart
 uuid-runtime
 apache2
 cmake
 cups-daemon
 gitweb
 apparmor
 lightdm
 mysql-server-5.7
 snap-confine
 ubuntu-core-launcher
 alsa-utils
 ubuntu-drivers-common
 whoopsie
 sendmail-bin
 libsolid4
 libkio5
 libakonadi-kde4
 libakonadi-kmime4
 libbaloofiles4
 libkabc4
 libkemoticons4
 libkpimutils4
 libkparts4
 libkdewebkit5
 libknewstuff3-4
 libplasma3
 baloo-utils
 libktexteditor4
 libkatepartinterfaces4
 katepart
 kdoctools
 libkde3support4
 libkfile4
 libkhtml5
 kdelibs5-plugins
 plasma-scriptengine-javascript
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

After 
```

apt-get --force-yes install cron
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cron is already the newest version (3.0pl1-128ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1228 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
```

Is there an easy fix.:confused:

Reg.

---

### Post by Impavidus on 2016-08-28
You may be able to repair this, but the easy fix is definitely a fresh install.

---

