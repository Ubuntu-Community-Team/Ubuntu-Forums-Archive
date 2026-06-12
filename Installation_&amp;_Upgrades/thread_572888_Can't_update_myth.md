---
title: "Can't update myth"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by little cazy on 2007-10-10
i can't update ubbuntu-mythtv-frontend and mythtv music.

---

### Post by tgm4883 on 2007-10-11
error messages?

---

### Post by little cazy on 2007-10-11
i couldn't copy paste but this was the next best thing.
it does not go any farther.

---

### Post by tgm4883 on 2007-10-11
What version of ubuntu are you running?

---

### Post by little cazy on 2007-10-11
read my signation. gutsy

---

### Post by tgm4883 on 2007-10-11
Hmm.

Have you tried apt-get dist-upgrade

---

### Post by little cazy on 2007-10-11
```
$ sudo apt-get dist-upgrade
[sudo] password for eyez:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  apparmor apparmor-utils startup-tasks system-services ubuntu-minimal upstart
  upstart-compat-sysv upstart-logd
The following NEW packages will be installed:
  sysvinit
The following packages have been kept back:
  mythmusic
The following packages will be upgraded:
  ubuntu-mythtv-frontend
1 upgraded, 1 newly installed, 8 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 110kB/291kB of archives.
After unpacking 4395kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/main sysvinit 2.86.ds1-14.1ubuntu31 [110kB]
Fetched 110kB in 1s (60.5kB/s)  
(Reading database ... 143734 files and directories currently installed.)
Removing apparmor-utils ...
Removing apparmor ...
Unloading AppArmor profiles : done.
update-initramfs: deferring update (trigger activated)
Removing ubuntu-minimal ...
Removing startup-tasks ...
Removing system-services ...
Removing upstart-logd ...
Removing upstart-compat-sysv ...
Removing upstart ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Selecting previously deselected package sysvinit.
(Reading database ... 143642 files and directories currently installed.)
Unpacking sysvinit (from .../sysvinit_2.86.ds1-14.1ubuntu31_i386.deb) ...
Setting up sysvinit (2.86.ds1-14.1ubuntu31) ...
init: timeout opening/writing control channel /dev/initctl

(Reading database ... 143671 files and directories currently installed.)
Preparing to replace ubuntu-mythtv-frontend 0.20.2+fixes14659-0ubuntu0~mythbuntu1 (using .../ubuntu-mythtv-frontend_0.20.2+fixes14659-0ubuntu0~mythbuntu1_all.deb) ...
Unpacking replacement ubuntu-mythtv-frontend ...
Setting up mythtv-backend (0.20.2+fixes14659-0ubuntu0~mythbuntu1) ...
udev active, devices will be created in /dev/.static/dev/
/etc/init.d/mythtv-backend: 77: own_firewire: not found
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error processing mythtv-backend (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-backend (= 0.20.2+fixes14659-0ubuntu0~mythbuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend (= 0.20.2+fixes14659-0ubuntu0~mythbuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntu-mythtv-frontend (0.20.2+fixes14659-0ubuntu0~mythbuntu1) ...

Errors were encountered while processing:
 mythtv-backend
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by little cazy on 2007-10-15
```
libflac7:

Package libflac7 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```
this was the big ploblem for me. i think

---

