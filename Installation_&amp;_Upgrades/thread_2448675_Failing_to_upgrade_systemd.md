---
title: "Failing to upgrade systemd"
date: 2020-08-11
forum: Installation &amp; Upgrades
---

### Post by dcourtney on 2020-08-11
Would appreciate some help with this, will continue to search for a solution but must be searching for the wrong keywords.

**What is wrong**: Can't successfully run sudo apt-get upgrade

**OS Version**:
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:        18.04
Codename:       bionic

**Error:**
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnss-systemd : Depends: systemd (= 237-3ubuntu10.42) but 237-3ubuntu10.38 is installed
 libpam-systemd : Depends: systemd (= 237-3ubuntu10.42) but 237-3ubuntu10.38 is installed
 systemd : Depends: libsystemd0 (= 237-3ubuntu10.38) but 237-3ubuntu10.42 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

$ sudo apt-get --fix-broken install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  systemd
Suggested packages:
  systemd-container
The following packages will be upgraded:
  systemd
1 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,914 kB of archives.
After this operation, 24.6 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 143098 files and directories currently installed.)
Preparing to unpack .../systemd_237-3ubuntu10.42_amd64.deb ...
Unpacking systemd (237-3ubuntu10.42) over (237-3ubuntu10.38) ...
dpkg: error processing archive /var/cache/apt/archives/systemd_237-3ubuntu10.42_amd64.deb (--unpack):
 unable to move aside './usr/share/zsh/vendor-completions/_systemd-delta' to install new version: Structure needs cleaning
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_237-3ubuntu10.42_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Thanks,
David

---

### Post by TheFu on 2020-08-12
I'd look through the **syslog** and **dmesg** output for errors and warnings. Depending on those, I'd try to fix any related to the packaging system or failing storage.  I always suspect failing storage - HDDs, cables, disk controllers.

I would try these things, in order:
```
sudo dpkg --configure -a
sudo apt-get install -f

```
Then I'd check that the system isn't out of storage.
```
df -Th
df -i
```
Look for any real storage at 100% - ignore all loop devices.  Free up at least 1G of storage for all OS partitions. If the inodes are low, you'll want to remove thousands and thousands of tiny files from somewhere - or move all those files to a different file system.

```
sudo rm  /var/cache/apt/archives/systemd_237-3ubuntu10.42_amd64.deb
sudo apt clean
sudo apt autoremove
sudo apt-get update
sudo apt-get full-upgrade
```

---

