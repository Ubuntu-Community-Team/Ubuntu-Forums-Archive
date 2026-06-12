---
title: "Upgrade to Bionic, unable to correct dependencies"
date: 2020-06-08
forum: Installation &amp; Upgrades
---

### Post by afrodeity on 2020-06-08
Upgraded my 32bit backup machine last night. Took a look this morning, and its got some weird dependency errors:

```
sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libudev-dev : Depends: libudev1 (= 237-3ubuntu10.41) but 229-4ubuntu21.28 is installed
 linux-tools-4.15.0-101-generic : Depends: linux-tools-4.15.0-101 but it is not installed
 systemd : Depends: libsystemd0 (= 229-4ubuntu21.28) but 237-3ubuntu10.41 is installed
 unity-greeter : Depends: upstart but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I also get an error about systemd-shm [ like this]("https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859")

---

### Post by afrodeity on 2020-06-08
```
sudo aptitude install libudev-dev
sudo aptitude install linux-tools-4.15.0-101-generic
```

```
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-tools-4.15.0-101-generic:
 linux-tools-4.15.0-101-generic depends on linux-tools-4.15.0-101; however:
  Package linux-tools-4.15.0-101 is not installed.

dpkg: error processing package linux-tools-4.15.0-101-generic (--configure):
 dependency problems - leaving unconfigured
Setting up systemd (237-3ubuntu10.41) ...
Synchronizing state of ondemand.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable ondemand
Unsafe symlinks encountered in /var/log/journal, refusing.
Unsafe symlinks encountered in /var/log/journal, refusing.
Unsafe symlinks encountered in /var/log/journal, refusing.
dpkg: error processing package systemd (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libpam-systemd:i386:
 libpam-systemd:i386 depends on systemd (= 237-3ubuntu10.41); however:
  Package systemd is not configured yet.

dpkg: error processing package libpam-systemd:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-session:
 indicator-session depends on libpam-systemd; however:
  Package libpam-systemd:i386 is not configured yet.

dpkg: error processing package indicator-session (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-tools-4.15.0-101-generic
 systemd
 libpam-systemd:i386
 indicator-session

```

stuck

---

### Post by afrodeity on 2020-06-08
```
cd /
chown root.root 
```

as in [this example]("https://askubuntu.com/questions/1094776/systemd-tmpfiles-wont-start")

then
```

sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-tools-4.15.0-101-generic:
 linux-tools-4.15.0-101-generic depends on linux-tools-4.15.0-101; however:
  Package linux-tools-4.15.0-101 is not installed.

dpkg: error processing package linux-tools-4.15.0-101-generic (--configure):
 dependency problems - leaving unconfigured
Setting up systemd (237-3ubuntu10.41) ...
Synchronizing state of ondemand.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable ondemand
Removing user `systemd-bus-proxy' ...
Warning: group `systemd-bus-proxy' has no more members.
Done.
[/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Unsafe symlinks encountered in /var/run/screen, refusing.
Unsafe symlinks encountered in /var/run/sshd, refusing.
Unsafe symlinks encountered in /var/run/sudo, refusing.
Unsafe symlinks encountered in /var/run/sudo/ts, refusing.
Unsafe symlinks encountered in /var/lib/systemd/coredump, refusing.
Removing obsolete conffile /etc/systemd/bootchart.conf ...
Removing obsolete conffile /etc/dbus-1/system.d/org.freedesktop.hostname1.conf ...
Removing obsolete conffile /etc/dbus-1/system.d/org.freedesktop.locale1.conf ...
Removing obsolete conffile /etc/dbus-1/system.d/org.freedesktop.login1.conf ...
Removing obsolete conffile /etc/dbus-1/system.d/org.freedesktop.network1.conf ...
Removing obsolete conffile /etc/dbus-1/system.d/org.freedesktop.resolve1.conf ...
Removing obsolete conffile /etc/dbus-1/system.d/org.freedesktop.systemd1.conf ...
Removing obsolete conffile /etc/dbus-1/system.d/org.freedesktop.timedate1.conf ...
Setting up libpam-systemd:i386 (237-3ubuntu10.41) ...
Setting up indicator-session (17.3.20+17.10.20171006-0ubuntu1) ...
Removing obsolete conffile /etc/xdg/autostart/indicator-session.desktop ...
Errors were encountered while processing:
 linux-tools-4.15.0-101-generic
```

---

### Post by afrodeity on 2020-06-08
then ```
sudo aptitude install linux-tools-4.15.0-101-generic
```
followed by apt install -f
no more problems it seems

---

