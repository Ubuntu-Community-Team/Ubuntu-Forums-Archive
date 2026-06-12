---
title: "Upgrading to Vivid and systemd won't install"
date: 2015-09-12
forum: Installation &amp; Upgrades
---

### Post by brianwc on 2015-09-12
I'm in the middle of an upgrade to Vivid. I have foolishly skipped a few releases--too late now. Here's the error I'm getting:

```
The following extra packages will be installed:
  systemd
The following NEW packages will be installed:
  systemd
0 upgraded, 1 newly installed, 0 to remove and 482 not upgraded.
14 not fully installed or removed.
Need to get 0 B/3,530 kB of archives.
After this operation, 18.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 415776 files and directories currently installed.)
Preparing to unpack .../systemd_219-7ubuntu6_amd64.deb ...
Unpacking systemd (219-7ubuntu6) ...
dpkg: error processing archive /var/cache/apt/archives/systemd_219-7ubuntu6_amd64.deb (--unpack):
 trying to overwrite '/usr/share/dbus-1/system-services/org.freedesktop.locale1.service', which is also in package ubuntu-system-service 0.2.2.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_219-7ubuntu6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas? The above is what happens when I do ```
apt-get -f install
``` and I've tried many times to do ```
dpkg --configure -a
``` but it has no positive effect.

---

