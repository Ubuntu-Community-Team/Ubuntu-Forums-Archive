---
title: "do-release-upgrade fails after 18.04.1 LTS"
date: 2018-08-18
forum: Installation &amp; Upgrades
---

### Post by tux43 on 2018-08-18
Hi, 
I've just tried to upgrade to 18.04.1 LTS from 18.04 LTS and I'm now stuck!

Here is what happens if I type the command.

```
root@ip-172-31-15-171:~# do-release-upgrade
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 11, in <module>
    from UpdateManager.Core.MetaRelease import MetaReleaseCore
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 25, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 23, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 11, in <module>
    from UpdateManager.Core.MetaRelease import MetaReleaseCore
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 25, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
root@ip-172-31-15-171:~# 
```

---

### Post by wildmanne39 on 2018-08-18
Hello, please do:
```
sudo apt update && sudo apt upgrade
```
Then try again, a few days ago an update was done to this package that fixes it where the upgrade works, unless there is a new issue that I am not aware of.

---

### Post by tux43 on 2018-08-18
Here is what happens. Thanks for your reply


```

root@ip-172-31-15-171:/backup_galactica/rootbin# sudo apt update
Hit:1 http://ap-southeast-2.ec2.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://ap-southeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:3 http://security.ubuntu.com/ubuntu bionic-security InRelease                
Reading package lists... Done                         
Building dependency tree       
Reading state information... Done
549 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@ip-172-31-15-171:/backup_galactica/rootbin# 



root@ip-172-31-15-171:/backup_galactica/rootbin# sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libpython3.6-stdlib : Depends: libreadline7 (>= 7.0~beta) but it is not installed
 mailutils : Depends: libmailutils5 but it is not installed
             Depends: libreadline7 (>= 6.0) but it is not installed
 python-apt : Depends: libapt-inst2.0 (>= 1.4~beta3) but 1.2.27 is installed
              Depends: libapt-pkg5.0 (>= 1.4~beta3) but 1.2.26 is installed
 python3-apt : Depends: libapt-inst2.0 (>= 1.4~beta3) but 1.2.27 is installed
               Depends: libapt-pkg5.0 (>= 1.4~beta3) but 1.2.26 is installed
 python3-cryptography : Depends: python3-asn1crypto (>= 0.21.0~) but it is not installed
                        Depends: python3-idna (>= 2.1) but 2.0-3 is installed
 python3-gdbm : Depends: libgdbm5 (>= 1.14) but it is not installed
 python3-systemd : Depends: libsystemd0 (>= 233) but 229-4ubuntu21.4 is installed
E: Unmet dependencies. Try using -f.
root@ip-172-31-15-171:/backup_galactica/rootbin# 
```

---

### Post by aysiu on 2018-08-18
Try ```
sudo apt -f install
```

---

### Post by tux43 on 2018-08-18
Got my self into a real mess. Considering restoring from backup. 

```
root@ip-172-31-15-171:/backkkkk/oldroot# apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cgmanager dh-python fonts-ubuntu-font-family-console libcryptsetup4 libxapian-1.3-5 python3-distutils python3-lib2to3
  python3.5 python3.5-minimal
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  apt apt-transport-https apt-utils libapt-inst2.0 libapt-pkg5.0 libgdbm5 libmailutils5 libpam-systemd libreadline7
  libsystemd0 python3-asn1crypto python3-idna systemd
Suggested packages:
  apt-doc aptitude | synaptic | wajig dpkg-dev gdbm-l10n systemd-container
Recommended packages:
  networkd-dispatcher
The following packages will be REMOVED:
  systemd-shim
The following NEW packages will be installed:
  libgdbm5 libmailutils5 libreadline7 python3-asn1crypto
The following packages will be upgraded:
  apt apt-transport-https apt-utils libapt-inst2.0 libapt-pkg5.0 libpam-systemd libsystemd0 python3-idna systemd
9 upgraded, 4 newly installed, 1 to remove and 540 not upgraded.
22 not fully installed or removed.
Need to get 0 B/6,152 kB of archives.
After this operation, 2,622 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 94991 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by aysiu on 2018-08-18
Try renaming that file, and then fixing again: ```
sudo mv /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.bak
sudo apt -f install
```

---

### Post by tux43 on 2018-08-19
Did that, gave up, restored the / file system and back up and running on 18.04. I'm going to leave 18.04.1 LTS for a while, hopefully things sort themselves out.

---

### Post by Impavidus on 2018-08-19
A couple of things:

There's no need to use sudo if you're using a root shell already. You did so in post 3, but not in the other posts, so you're probably aware of that.

There's no release upgrade available from 18.04 to 18.04.1 because that's the same release. 18.04.1 is just a new live disk image file, which includes the bugfixes released since the original release of 18.04. If you just install all regular upgrades, your 18.04 becomes 18.04.1 automatically. If you try do-release-upgrade from 18.04, it will upgrade you to 18.10 (but only if you allow upgrades to development versions).

I see a remarkable number of partially installed packages and available upgrades. If your restore from a backup didn't fix that, I suggest you fix that right away.

---

### Post by tux43 on 2018-08-22
> **Impavidus said:**
> 
There's no release upgrade available from 18.04 to 18.04.1 because that's the same release. 18.04.1 is just a new live disk image file, which includes the bugfixes released since the original release of 18.04. If you just install all regular upgrades, your 18.04 becomes 18.04.1 automatically. If you try do-release-upgrade from 18.04, it will upgrade you to 18.10 (but only if you allow upgrades to development versions).


You are correct, I am currently on 16.04.5 LTS and trying to go to 18.04.1 LTS. Is this risky, too bigger jump?
BTW: My restore worked therefore stress levels have subsided. Any tips on 18.04.1 upgrade?

---

### Post by tux43 on 2018-08-23
Hi,

I've cloned the machine and attempted to do an upgrade with exactly the same error.

Here is the exit status after do-release-upgrade fails.

```
root@ip-172-31-1-49:~# do-release-upgrade 
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]                                           
Get:2 Upgrade tool [1,258 kB]                                                  
Fetched 1,258 kB in 0s (0 B/s)                                                 
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg' 
extracting 'bionic.tar.gz'

 libpython3.6-stdlib:amd64
 python3.6
 python3-apt
 python3
 python3-cffi-backend
 apt-xapian-index
 python3-xapian
 python3-gi
 mailutils
 python3-markupsafe
 python3-systemd
 python3-gdbm:amd64
 python3-lib2to3
 python-apt
 dh-python
 python3-distutils
 libpython3-stdlib:amd64
 python3-yaml
 python3-pycurl
 python3-dbus

Upgrade complete

The upgrade has completed but there were errors during the upgrade
process.

To continue please press [ENTER]
=== Command terminated with exit status 1 (Thu Aug 23 22:07:50 2018) ===
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-r6mbnigl/bionic", line 3, in <module>
    from DistUpgrade.DistUpgradeMain import main
  File "/tmp/ubuntu-release-upgrader-r6mbnigl/DistUpgrade/DistUpgradeMain.py", line 22, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 23, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference

Original exception was:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-r6mbnigl/bionic", line 3, in <module>
    from DistUpgrade.DistUpgradeMain import main
  File "/tmp/ubuntu-release-upgrader-r6mbnigl/DistUpgrade/DistUpgradeMain.py", line 22, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
=== Command detached from window (Thu Aug 23 22:07:57 2018) ===
=== Command terminated with exit status 1 (Thu Aug 23 22:08:07 2018) ===
```

---

### Post by dragans2 on 2018-08-25
hi tux43, today I ran [FONT=courier new]do-release-upgrade[/FONT] in Ubuntu 16 and ended in the same situation as mentioned above (same unmet dependencies).

What helped me:
[LIST=1]
[*]to use [FONT=courier new]sudo dpkg --remove [package-name][/FONT] to remove problematic packages found via [FONT=courier new]sudo dpkg --configure -a[/FONT] (source: [https://stackoverflow.com/a/35969176/557223](https://stackoverflow.com/a/35969176/557223) ). Some packages couldn't be removed as they were dependencies of another packages.
[*]to run [FONT=courier new]sudo apt-get install -f[/FONT] (it started to working again, yay)
[*]to rename [FONT=courier new]org.freedesktop.systemd1.service[/FONT] file as mentioned above and also mentioned in [https://askubuntu.com/a/838673](https://askubuntu.com/a/838673)
[*]to run [FONT=courier new]sudo apt-get update[/FONT] and [FONT=courier new]dist-upgrade[/FONT] and [FONT=courier new]autoremove[/FONT]
[*]to finally eat some food, since I was very hungry due to solving the issue
[/LIST]

---

### Post by jokker on 2018-11-04
> **aysiu said:**
> Try renaming that file, and then fixing again: ```
sudo mv /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.bak
sudo apt -f install
```

Hello,

I had the exact same issue on release upgrade and renaming > /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service worked like a charm, thanks for that

---

### Post by iamquang95 on 2019-01-22
Hello, i may have the same error, tried many way but i still can't fix the problem

```

sudo apt-get update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release
Hit:3 https://dl.yarnpkg.com/debian stable InRelease
Hit:5 https://deb.nodesource.com/node_10.x bionic InRelease
Hit:7 https://download.docker.com/linux/ubuntu bionic InRelease
Hit:8 http://vn.archive.ubuntu.com/ubuntu bionic InRelease
Get:9 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Hit:10 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease
Hit:11 http://vn.archive.ubuntu.com/ubuntu bionic-updates InRelease
Get:12 http://vn.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Hit:6 https://packages.cloud.google.com/apt kubernetes-xenial InRelease
Fetched 158 kB in 2s (92.0 kB/s)
Error: Timeout was reached
Traceback (most recent call last):
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN9pkgSystem9LockInnerEv version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 24, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN9pkgSystem9LockInnerEv version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference


Original exception was:
Traceback (most recent call last):
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN9pkgSystem9LockInnerEv version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code

```

Do anyone know hot to fix this problem ?

---

