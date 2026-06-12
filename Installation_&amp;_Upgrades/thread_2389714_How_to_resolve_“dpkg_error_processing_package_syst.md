---
title: "How to resolve “dpkg: error processing package systemd”"
date: 2018-04-20
forum: Installation &amp; Upgrades
---

### Post by fun9990 on 2018-04-20
After upgrade from Ubuntu 16 to Ubuntu 18
When I want to use this command:




```

apt-get -f install

```
I see this output:




```

dpkg: error processing package systemd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 systemd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
And




```

 dpkg --configure -a

```
Output is:




```

Errors were encountered while processing:
 python3-numpy
 libc-bin
 systemd
 python3-gdbm:amd64
 python3-cairo:amd64
 python3-tk:amd64
 python3-matplotlib
 dh-python
 libglib2.0-bin
 locales
 libpam-systemd:amd64

```
```

 python
Python 2.7.12 (default, Dec  4 2017, 14:50:18)

```
And




```

python3
Python 3.6.5 (default, Apr  1 2018, 05:46:30)

```
And install any package for example: apt install systemd Output is:




```

 python3-cairo : Depends: python3 (>= 3.6~) but 3.5.1-3 is to be installed
 python3-gdbm : Depends: python3 (>= 3.6.4-1~) but 3.5.1-3 is to be installed
 python3-matplotlib : Depends: python3 (>= 3.6~) but 3.5.1-3 is to be installed
 python3-numpy : Depends: python3 (>= 3.6~) but 3.5.1-3 is to be installed
 python3-tk : Depends: python3 (>= 3.6.4-1~) but 3.5.1-3 is to be installed

```
Any suggestions?

---

### Post by deadflowr on 2018-04-20
> python3-cairo : Depends: python3 (>= 3.6~) but 3.5.1-3 is to be installed
Somehow your system is not up-to-date, package listings wise.
How did you update from 16.04 to 18.04?

What does
```
sudo apt update
```
output?

---

### Post by fun9990 on 2018-04-21
my way was:
sudo apt update 
sudo apt upgrade
sudo apt dist-upgrade
sudo apt install update-manager-core
sudo do-release-upgrade
sudo do-release-upgrade -d

And: 
root@win:~# sudo apt update
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease [235 kB]
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main amd64 Packages [1021 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main Translation-en [517 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages [8561 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe Translation-en [4941 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/multiverse amd64 Packages [151 kB]
Fetched 15.4 MB in 1min 14s (206 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
1982 packages can be upgraded. Run 'apt list --upgradable' to see them.

---

### Post by deadflowr on 2018-04-21
> 1982 packages can be upgraded. Run 'apt list --upgradable' to see them.
Then there is your answer.
For some reason or another the upgrade must not have ran as it should have.

No reason for that to result in any more than a couple dozen to couple hundred new updates at most. 
But 1900+ means it wasn't a proper upgrade or something wrong happened during the upgrade.

So what does
```
sudo apt full-upgrade
```
do/show?
(This would be more for a curiosity stand point, and feel free to select n to abort.
I'm more interested in seeing what the output of install.upgrade/remove will be)

---

### Post by fun9990 on 2018-04-22
this command output is:
```

root@win:~# sudo apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 dh-python : Depends: python3-distutils but it is not installed
 indicator-session : Depends: systemd-services but it is not installable
 libc-bin : Depends: libc6 (< 2.24) but 2.27-3ubuntu1 is installed
 libc-dev-bin : Depends: libc6 (< 2.24) but 2.27-3ubuntu1 is installed
 libc6-dbg : Depends: libc6 (= 2.23-0ubuntu10) but 2.27-3ubuntu1 is installed
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu10) but 2.27-3ubuntu1 is installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.56.1-2ubuntu1) but 2.48.2-0ubuntu1 is installed
 libglib2.0-dev : Depends: libglib2.0-bin (= 2.48.2-0ubuntu1) but 2.56.1-2ubuntu1 is installed
 locales : Depends: libc-bin (> 2.27) but 2.23-0ubuntu10 is installed
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.6.5-3 is installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.6.5-3 is installed
 python3-cairo : Depends: python3 (>= 3.6~) but 3.5.1-3 is installed
 python3-gdbm : Depends: python3 (>= 3.6.4-1~) but 3.5.1-3 is installed
 python3-matplotlib : Depends: python3 (>= 3.6~) but 3.5.1-3 is installed
 python3-numpy : Depends: python3 (>= 3.6~) but 3.5.1-3 is installed
 python3-tk : Depends: python3 (>= 3.6.4-1~) but 3.5.1-3 is installed
 udev : Depends: libudev1 (= 229-4ubuntu21.2) but 237-3ubuntu8 is installed
E: Unmet dependencies. Try using -f.

```

and additional results are in my first post

---

### Post by fun9990 on 2018-04-24
Up and be ready!

---

### Post by deadflowr on 2018-04-24
Well let's see how far along the upgrade actually got
what do
```
uname -r
lsb_release -a

```
show.

Also release upgrade have logs in /var/log/dist-upgrade.
Look at what main.log shows at the end.
```
tail -n 100 /var/log/dist-upgrade/main.log
```
you might also check what the ends of the apt.log, history.log, and term.log files show.
You can use the same tail command and simply change out the file name.

---

### Post by fun9990 on 2018-04-24
```
root@win:/var/log/dist-upgrade# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu Bionic Beaver (development branch)
Release:        18.04
Codename:       bionic

```

And:

 ```
root@win:/var/log/dist-upgrade# tail -l apt-term.log
Executing: /lib/systemd/systemd-sysv-install enable ondemand
[/usr/lib/tmpfiles.d/tmp.conf:15] Failed to replace specifiers: /tmp/systemd-private-%b-*
[/usr/lib/tmpfiles.d/tmp.conf:16] Failed to replace specifiers: /tmp/systemd-private-%b-*/tmp
[/usr/lib/tmpfiles.d/tmp.conf:17] Failed to replace specifiers: /var/tmp/systemd-private-%b-*
[/usr/lib/tmpfiles.d/tmp.conf:18] Failed to replace specifiers: /var/tmp/systemd-private-%b-*/tmp
dpkg: error processing package systemd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 systemd
Log ended: 2018-04-20  20:53:47
```

And:


```
root@win:/var/log/dist-upgrade# tail -100 apt.log
Investigating (0) php-bz2 [ amd64 ] < none -> 1:7.2+60ubuntu1 > ( universe/php )
Broken php-bz2:amd64 Depends on php7.2-bz2 [ amd64 ] < none -> 7.2.3-1ubuntu1 > ( universe/php )
  Considering php7.2-bz2:amd64 1 as a solution to php-bz2:amd64 0
  MarkKeep php-bz2 [ amd64 ] < none -> 1:7.2+60ubuntu1 > ( universe/php ) FU=0
  Holding Back php-bz2:amd64 rather than change php7.2-bz2:amd64
Investigating (0) libcurl4-openssl-dev [ amd64 ] < 7.47.0-1ubuntu2.7 -> 7.58.0-2ubuntu3 > ( libdevel )
Broken libcurl4-openssl-dev:amd64 Depends on libcurl4 [ amd64 ] < none -> 7.58.0-2ubuntu3 > ( libs ) (= 7.58.0-2ubuntu3)
  Considering libcurl4:amd64 -1 as a solution to libcurl4-openssl-dev:amd64 0
  MarkKeep libcurl4-openssl-dev [ amd64 ] < 7.47.0-1ubuntu2.7 -> 7.58.0-2ubuntu3 > ( libdevel ) FU=0
  Removing libcurl4-openssl-dev:amd64 rather than change libcurl4:amd64
  MarkDelete libcurl4-openssl-dev [ amd64 ] < 7.47.0-1ubuntu2.7 -> 7.58.0-2ubuntu3 > ( libdevel ) FU=0
Investigating (0) libqalculate6-data [ amd64 ] < none -> 0.9.10-1 > ( universe/libs )
Broken libqalculate6-data:amd64 Breaks on libqalculate5-data [ amd64 ] < 0.9.7-9.1 > ( libs )
  Considering libqalculate5-data:amd64 -2 as a solution to libqalculate6-data:amd64 0
  Added libqalculate5-data:amd64 to the remove list
  Fixing libqalculate6-data:amd64 via remove of libqalculate5-data:amd64
  MarkDelete libqalculate5-data [ amd64 ] < 0.9.7-9.1 > ( libs ) FU=0
Investigating (0) cmake [ amd64 ] < 3.5.1-1ubuntu3 -> 3.10.2-1ubuntu1 > ( devel )
Broken cmake:amd64 Depends on libcurl4 [ amd64 ] < none -> 7.58.0-2ubuntu3 > ( libs ) (>= 7.16.2)
  Considering libcurl4:amd64 -1 as a solution to cmake:amd64 0
  MarkKeep cmake [ amd64 ] < 3.5.1-1ubuntu3 -> 3.10.2-1ubuntu1 > ( devel ) FU=0
  Removing cmake:amd64 rather than change libcurl4:amd64
  MarkDelete cmake [ amd64 ] < 3.5.1-1ubuntu3 -> 3.10.2-1ubuntu1 > ( devel ) FU=0
Investigating (0) libmagickwand-6.q16-2 [ amd64 ] < 8:6.8.9.9-7ubuntu5.9 > ( libs )
Broken libmagickwand-6.q16-2:amd64 Depends on libmagickcore-6.q16-2 [ amd64 ] < 8:6.8.9.9-7ubuntu5.9 > ( libs ) (>= 8:6.8.9.9)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to libmagickwand-6.q16-2:amd64 0
  Removing libmagickwand-6.q16-2:amd64 rather than change libmagickcore-6.q16-2:amd64
  MarkDelete libmagickwand-6.q16-2 [ amd64 ] < 8:6.8.9.9-7ubuntu5.9 > ( libs ) FU=0
Investigating (0) pollinate [ amd64 ] < 4.25-0ubuntu1~16.04.1 -> 4.31-0ubuntu1 > ( admin )
Broken pollinate:amd64 Depends on curl [ amd64 ] < 7.47.0-1ubuntu2.7 -> 7.58.0-2ubuntu3 > ( web )
  Considering curl:amd64 12 as a solution to pollinate:amd64 0
  MarkKeep pollinate [ amd64 ] < 4.25-0ubuntu1~16.04.1 -> 4.31-0ubuntu1 > ( admin ) FU=0
  Removing pollinate:amd64 rather than change curl:amd64
  MarkDelete pollinate [ amd64 ] < 4.25-0ubuntu1~16.04.1 -> 4.31-0ubuntu1 > ( admin ) FU=0
Investigating (0) libwebkitgtk-1.0-0 [ amd64 ] < 2.4.11-0ubuntu0.1 -> 2.4.11-3ubuntu3 > ( universe/libs )
Broken libwebkitgtk-1.0-0:amd64 Breaks on libwebkitgtk-1.0-common [ amd64 ] < 2.4.11-0ubuntu0.1 > ( libs ) (< 2.4.11-2~)
  Considering libwebkitgtk-1.0-common:amd64 -3 as a solution to libwebkitgtk-1.0-0:amd64 0
  Added libwebkitgtk-1.0-common:amd64 to the remove list
  Fixing libwebkitgtk-1.0-0:amd64 via remove of libwebkitgtk-1.0-common:amd64
  MarkDelete libwebkitgtk-1.0-common [ amd64 ] < 2.4.11-0ubuntu0.1 > ( libs ) FU=0
Investigating (0) perl-modules-5.22 [ amd64 ] < 5.22.1-9ubuntu0.3 > ( perl )
Broken perl-modules-5.22:amd64 Conflicts on perl-modules [ amd64 ] < none ->  > ( none )
  Considering perl-modules-5.26:amd64 115 as a solution to perl-modules-5.22:amd64 -1
  Removing perl-modules-5.22:amd64 rather than change perl-modules:amd64
  MarkDelete perl-modules-5.22 [ amd64 ] < 5.22.1-9ubuntu0.3 > ( perl ) FU=0
Investigating (0) linuxbrew-wrapper [ amd64 ] < 20150804-3 -> 20170516-2 > ( universe/utils )
Broken linuxbrew-wrapper:amd64 Depends on curl [ amd64 ] < 7.47.0-1ubuntu2.7 -> 7.58.0-2ubuntu3 > ( web )
  Considering curl:amd64 12 as a solution to linuxbrew-wrapper:amd64 -1
  MarkKeep linuxbrew-wrapper [ amd64 ] < 20150804-3 -> 20170516-2 > ( universe/utils ) FU=0
  Removing linuxbrew-wrapper:amd64 rather than change curl:amd64
  MarkDelete linuxbrew-wrapper [ amd64 ] < 20150804-3 -> 20170516-2 > ( universe/utils ) FU=0
Investigating (0) libvlccore8 [ amd64 ] < 2.2.2-5ubuntu0.16.04.4 > ( libs )
Broken libvlccore8:amd64 Depends on vlc-data [ amd64 ] < 2.2.2-5ubuntu0.16.04.4 -> 3.0.1-3build1 > ( universe/graphics ) (= 2.2.2-5ubuntu0.16.04.4)
  Considering vlc-data:amd64 2 as a solution to libvlccore8:amd64 -1
  Removing libvlccore8:amd64 rather than change vlc-data:amd64
  MarkDelete libvlccore8 [ amd64 ] < 2.2.2-5ubuntu0.16.04.4 > ( libs ) FU=0
Investigating (0) libperl5.22 [ amd64 ] < 5.22.1-9ubuntu0.3 > ( libs )
Broken libperl5.22:amd64 Depends on perl-modules-5.22 [ amd64 ] < 5.22.1-9ubuntu0.3 > ( perl ) (>= 5.22.1-9ubuntu0.3)
  Considering perl-modules-5.22:amd64 -1 as a solution to libperl5.22:amd64 -2
  Removing libperl5.22:amd64 rather than change perl-modules-5.22:amd64
  MarkDelete libperl5.22 [ amd64 ] < 5.22.1-9ubuntu0.3 > ( libs ) FU=0
Investigating (0) libmagickcore-6.q16-2-extra [ amd64 ] < 8:6.8.9.9-7ubuntu5.9 > ( libs )
Broken libmagickcore-6.q16-2-extra:amd64 Depends on libmagickcore-6.q16-2 [ amd64 ] < 8:6.8.9.9-7ubuntu5.9 > ( libs ) (>= 8:6.8.9.9)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to libmagickcore-6.q16-2-extra:amd64 -2
  Removing libmagickcore-6.q16-2-extra:amd64 rather than change libmagickcore-6.q16-2:amd64
  MarkDelete libmagickcore-6.q16-2-extra [ amd64 ] < 8:6.8.9.9-7ubuntu5.9 > ( libs ) FU=0
Investigating (0) pulseaudio-module-x11 [ amd64 ] < 1:8.0-0ubuntu3.8 > ( sound )
Broken pulseaudio-module-x11:amd64 Depends on libpulse0 [ amd64 ] < 1:8.0-0ubuntu3.8 -> 1:11.1-1ubuntu7 > ( libs ) (= 1:8.0-0ubuntu3.8)
  Considering libpulse0:amd64 137 as a solution to pulseaudio-module-x11:amd64 -2
  Removing pulseaudio-module-x11:amd64 rather than change libpulse0:amd64
  MarkDelete pulseaudio-module-x11 [ amd64 ] < 1:8.0-0ubuntu3.8 > ( sound ) FU=0
Investigating (0) xserver-xorg-input-vmmouse [ amd64 ] < 1:13.1.0-1ubuntu2 > ( x11 )
Broken xserver-xorg-input-vmmouse:amd64 Depends on xorg-input-abi-22 [ amd64 ] < none ->  > ( none )
  Considering xserver-xorg-core:amd64 29 as a solution to xserver-xorg-input-vmmouse:amd64 -2
  Removing xserver-xorg-input-vmmouse:amd64 rather than change xorg-input-abi-22:amd64
  MarkDelete xserver-xorg-input-vmmouse [ amd64 ] < 1:13.1.0-1ubuntu2 > ( x11 ) FU=0
Investigating (0) libnss3-nssdb [ amd64 ] < 2:3.28.4-0ubuntu0.16.04.3 > ( admin )
Broken libnss3-nssdb:amd64 Depends on libnss3 [ amd64 ] < 2:3.28.4-0ubuntu0.16.04.3 -> 2:3.35-2ubuntu2 > ( libs ) (= 2:3.28.4-0ubuntu0.16.04.3)
  Considering libnss3:amd64 43 as a solution to libnss3-nssdb:amd64 -2
  Removing libnss3-nssdb:amd64 rather than change libnss3:amd64
  MarkDelete libnss3-nssdb [ amd64 ] < 2:3.28.4-0ubuntu0.16.04.3 > ( admin ) FU=0
Investigating (0) libmagick++-6.q16-5v5 [ amd64 ] < 8:6.8.9.9-7ubuntu5.9 > ( libs )
Broken libmagick++-6.q16-5v5:amd64 Depends on libmagickcore-6.q16-2 [ amd64 ] < 8:6.8.9.9-7ubuntu5.9 > ( libs ) (>= 8:6.8.9.9)
  Considering libmagickcore-6.q16-2:amd64 0 as a solution to libmagick++-6.q16-5v5:amd64 -2
  Removing libmagick++-6.q16-5v5:amd64 rather than change libmagickcore-6.q16-2:amd64
  MarkDelete libmagick++-6.q16-5v5 [ amd64 ] < 8:6.8.9.9-7ubuntu5.9 > ( libs ) FU=0
Investigating (0) libmetacity-private3a [ amd64 ] < 1:3.18.7-0ubuntu0.3 > ( libs )
Broken libmetacity-private3a:amd64 Depends on metacity-common [ amd64 ] < 1:3.18.7-0ubuntu0.3 -> 1:3.28.0-1 > ( universe/misc ) (= 1:3.18.7-0ubuntu0.3)
  Considering metacity-common:amd64 1 as a solution to libmetacity-private3a:amd64 -2
  Removing libmetacity-private3a:amd64 rather than change metacity-common:amd64
  MarkDelete libmetacity-private3a [ amd64 ] < 1:3.18.7-0ubuntu0.3 > ( libs ) FU=0
Investigating (0) libqalculate5v5 [ amd64 ] < 0.9.7-9.1 > ( libs )
Broken libqalculate5v5:amd64 Depends on libqalculate5-data [ amd64 ] < 0.9.7-9.1 > ( libs )
  Considering libqalculate5-data:amd64 -2 as a solution to libqalculate5v5:amd64 -2
  Removing libqalculate5v5:amd64 rather than change libqalculate5-data:amd64
  MarkDelete libqalculate5v5 [ amd64 ] < 0.9.7-9.1 > ( libs ) FU=0
Done
dmesg: read kernel buffer failed: Function not implemented
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
```




And:

```
root@win:/var/log/dist-upgrade# tail -l main.log
2018-04-20 20:53:46,893 ERROR got an error from dpkg for pkg: 'systemd': 'subprocess installed post-installation script returned error exit status 1'
2018-04-20 20:53:46,894 DEBUG running apport_pkgfailure() systemd: subprocess installed post-installation script returned error exit status 1
2018-04-20 20:53:50,130 ERROR Exception during pm.DoInstall()
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-ikiurxn3/DistUpgrade/DistUpgradeView.py", line 218, in run
    res = pm.do_install(self.writefd)
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
2018-04-20 20:53:50,197 ERROR SystemError from cache.commit(): installArchives() failed
2018-04-20 20:53:50,198 ERROR found exception: 'E:Sub-process /usr/bin/dpkg returned an error code (1)'
2018-04-20 20:54:20,728 DEBUG Running PostInstallScript: './xorg_fix_proprietary.py'
```

---

### Post by deadflowr on 2018-04-24
This isn't by chance related to Windows Subsystem for Linux?
Seems the systemd error is common for that.

---

### Post by fun9990 on 2018-04-24
yes, this is WSL
How can I resolve that?

---

### Post by deadflowr on 2018-04-25
Unfortunately WSL is beyond me as I don't, and possibly never will, use it.

Here a somewhat related bug:
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1757538]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1757538")
and related bug report with a possible workaround fix:
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1748659]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1748659")

Of course maybe you already got those patches, so it might not be working as expected.

Sorry, that's about the best I can do.

---

### Post by fun9990 on 2018-04-25
now can I go back to Ubuntu 16?

---

### Post by deadflowr on 2018-04-25
Only by uninstalling and reinstalling:
[https://www.howtogeek.com/261188/how-to-uninstall-or-reinstall-windows-10s-ubuntu-bash-shell/]("https://www.howtogeek.com/261188/how-to-uninstall-or-reinstall-windows-10s-ubuntu-bash-shell/")

---

