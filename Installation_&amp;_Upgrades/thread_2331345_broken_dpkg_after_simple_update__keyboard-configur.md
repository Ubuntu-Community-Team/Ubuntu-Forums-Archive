---
title: "broken dpkg after simple update : keyboard-configuration update FAIL"
date: 2016-07-21
forum: Installation &amp; Upgrades
---

### Post by allaf on 2016-07-21
hi,

On a fresh install of Ubuntu 16.04.1, at the first update apt-get upgrade fails:

```

root@pc:/home/user# aptitude upgrade
The following partially installed packages will be configured:
  console-setup console-setup-linux keyboard-configuration xserver-xorg-core 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up keyboard-configuration (1.108ubuntu15.2) ...
git: 'LC_CTYPE=fr_FR.UTF-8' is not a git command. See 'git --help'.
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of console-setup-linux:
 console-setup-linux depends on keyboard-configuration (= 1.108ubuntu15.2); however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on console-setup-linux; however:
  Package console-setup-linux is not configured yet.
 console-setup depends on keyboard-configuration (= 1.108ubuntu15.2); however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                      No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                                No apport report written because MaxReports is reached already
                                           problems - leaving unconfigured
Errors were encountered while processing:
 keyboard-configuration
 console-setup-linux
 console-setup
 xserver-xorg-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
Failed to perform requested operation on package.  Trying to recover:
Setting up keyboard-configuration (1.108ubuntu15.2) ...
git: 'LC_CTYPE=fr_FR.UTF-8' is not a git command. See 'git --help'.
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup-linux:
 console-setup-linux depends on keyboard-configuration (= 1.108ubuntu15.2); however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on console-setup-linux; however:
  Package console-setup-linux is not configured yet.
 console-setup depends on keyboard-configuration (= 1.108ubuntu15.2); however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 keyboard-configuration
 xserver-xorg-core
 console-setup-linux
 console-setup


```


```

# dpkg-reconfigure keyboard-configuration
/usr/sbin/dpkg-reconfigure: keyboard-configuration is broken or not fully installed

```

---

### Post by haarspalter on 2016-08-06
same problem here after upgrade 14.04 to [COLOR=#000000]16.04.1. Any solution yet for this?[/COLOR]

---

### Post by louisJ on 2016-10-05
Same issue here upgrading from 14.04 to 16?04....any fix please ??

---

### Post by tms95 on 2016-11-21
Same problem when trying to upgrade from 14.04 t 16.04. During upgrade, I got into an endless loop asking again and again for the language setting, several times per package, and neither ok nor cancel helped. Dozens of packages remained un-configured and the system was not usable, even though the desktop appeared after reboot.
 
I did a fresh install.

Installation was fine on the first machine.

On the second machine, the language was set up correctly, but the keyboard layout was wrong and could not be changed with the system settings (language support was installed). So I did a dpkg-reconfigure to fix the keyboard layout.

My recommendation: Backup the home folder and do a fresh install.

---

