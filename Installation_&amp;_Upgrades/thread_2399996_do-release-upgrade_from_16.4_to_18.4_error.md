---
title: "do-release-upgrade from 16.4 to 18.4 error"
date: 2018-09-01
forum: Installation &amp; Upgrades
---

### Post by ian dobson on 2018-09-01
Hi All,

I've tried to upgrade my old 16.4 System to 18.4 using do-release-upgrade, which crashed after about 30 minutes (download finished) just after asking afew questions about the kerbus Server. Sorry I don't have the exact error message.

If I rerun do-release-upgrade I get the following error:-
 ```

do-release-upgrade
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 11, in <module>
    from UpdateManager.Core.MetaRelease import MetaReleaseCore
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 25, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
root@alpha2:~#

```

if I run apt-get -f install I get
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cgmanager dh-python libgmp-dev libgnutlsxx28 libidn11:i386 libidn11-dev linux-headers-4.4.0-131 linux-headers-4.4.0-131-generic
  linux-image-4.4.0-131-generic linux-image-extra-4.4.0-131-generic nettle-dev
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  apt apt-transport-https apt-utils libapt-inst2.0 libapt-pkg5.0 libpam-systemd libudev1 libudev1:i386 networkd-dispatcher systemd udev
Suggested packages:
  apt-doc aptitude | synaptic | wajig systemd-container
The following packages will be REMOVED:
  systemd-shim
The following NEW packages will be installed:
  networkd-dispatcher
The following packages will be upgraded:
  apt apt-transport-https apt-utils libapt-inst2.0 libapt-pkg5.0 libpam-systemd libudev1 libudev1:i386 systemd udev
10 upgraded, 1 newly installed, 1 to remove and 1573 not upgraded.
3 not fully installed or removed.
Need to get 0 B/6,460 kB of archives.
After this operation, 4,741 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 237771 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 installed systemd-shim package post-removal script subprocess returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone got a tip how I can fix this?

Regards
Ian Dobson

---

### Post by ian dobson on 2018-09-01
Hi All,

OK I renamed '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' and re-ran "apt-get dist upgrade" which is now running.

Regards
Ian Dobson

---

### Post by ian dobson on 2018-09-02
OK the update appears to have worked.

I still have afew dependancy Problems with various perl modules, but that happens after each Major update.

Regards
Ian Dobson

---

