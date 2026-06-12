---
title: "Anyone else having problems with ubuntustudio-default-settings?"
date: 2009-06-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by camper365 on 2009-06-19
I tried to uninstall ubuntustudio-default-settings and it worked. However, when I tried to reinstall it (because I like the default settings, I was just trying to make it so that a new user would have the ubuntu default settings) it didn't completely install. I tried to purge it, but it tells methat it is in an unstable state and I should reinstall it before purging it. The problem is that I can't reinstall it. Is anyone else having this problem? Any idea how to fix it? Here is the terminal output whenever I run apt (note that the program hello is already installed on my system):
```
aaron@truman:~$ sudo aptitude install hello
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REMOVED:
  python-qt4-common{u} 
The following partially installed packages will be configured:
  ubuntustudio-desktop 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/6548B of archives. After unpacking 139kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 207772 files and directories currently installed.)
Preparing to replace ubuntustudio-default-settings 0.26 (using .../ubuntustudio-default-settings_0.26_all.deb) ...
Unpacking replacement ubuntustudio-default-settings ...
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/ubuntustudio-default-settings_0.26_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntustudio-default-settings_0.26_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntustudio-desktop:
 ubuntustudio-desktop depends on ubuntustudio-default-settings; however:
  Package ubuntustudio-default-settings is not installed.
dpkg: error processing ubuntustudio-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntustudio-desktop
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

aaron@truman:~$ 


```

---

### Post by camper365 on 2009-06-20
bump

---

### Post by camper365 on 2009-06-27
bump

---

### Post by lonniehenry on 2009-06-27
Yes I have the same problem and see a bug on launchpad, but have no solution to the problem.

---

### Post by dinxter on 2009-06-28
ubuntustudio-default-settings/karmic uptodate 0.26

/var/lib/dpkg/info/ubuntustudio-default-settings.postrm

```
#!/bin/sh

set -e

# Automatically added by dh_gconf
if which update-gconf-defaults >/dev/null 2>&1; then
        update-gconf-defaults
fi
# End automatically added section


rm -f /usr/share/gconf/defaults/21_ubuntustudio-panel-settings.entries
[ -x /usr/bin/update-gconf-defaults ] && update-gconf-defaults

```

the line 

[ -x /usr/sbin/update-gconf-defaults ] && update-gconf-defaults

should be,

[ -x /usr/bin/update-gconf-defaults ] && update-gconf-defaults

update-gconf-defaults is in /usr/bin not /usr/sbin

---

### Post by lonniehenry on 2009-06-28
Thanks, dinxter.  The change in the file cleared the error.  Had been puzzling over it for days.

---

### Post by untouch on 2009-09-05
thanks for this ... /bin 

so i can fix this, :D

---

### Post by blueglow on 2009-10-06
@ dinxter - Thanks! Worked like a dream on toast. I added your fix to the bug report at: [https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-default-settings/+bug/410867](https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-default-settings/+bug/410867)

---

### Post by fcastillo on 2009-10-09
Saved my life!!! Thanks soooooooooo much!!!

---

