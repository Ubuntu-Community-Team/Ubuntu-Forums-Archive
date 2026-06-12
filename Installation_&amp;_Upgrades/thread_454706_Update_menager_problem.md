---
title: "Update menager problem"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by jazzybob on 2007-05-25
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package hptsvr-https needs to be reinstalled, but I can't find an archive for it.'

---

### Post by taurus on 2007-05-25
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by tripolitan on 2007-05-27
there have been a few of these lately. I'm having the same problem with apt, aptitude and synaptic. Same error, none of the apt options work, cannot update, upgrade, re-install, install or remove or purge.
```
dpkg: error processing oss-linux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Ouch!  Got SIGABRT, dying..
Aborted

```

---

### Post by tripolitan on 2007-05-27
more related errors ```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report
```

---

### Post by taurus on 2007-05-27
> **tripolitan said:**
> more related errors ```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report
```

```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by tripolitan on 2007-05-27
> **taurus said:**
> ```
sudo dpkg --configure -a
sudo aptitude update
```
root@amdsmp:/home# sudo dpkg --configure -a
dpkg: error processing oss-linux (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 oss-linux

really frustrating :]

---

### Post by taurus on 2007-05-27
```
sudo aptitude --purge remove oss-linux
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by tripolitan on 2007-05-27
root@amdsmp:/home# aptitude --purge remove oss-linux
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages will be REMOVED:
  oss-linux
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 7377kB will be freed.
Writing extended state information... Done
dpkg: error processing oss-linux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
root@amdsmp:/home# Errors were encountered while processing:
 oss-linux

---

### Post by taurus on 2007-05-27
Were you trying to install oss-linux before?  And how did you try to install it?

---

### Post by tripolitan on 2007-05-27
I tried to install the pachage from 4front 
[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)
I selected x86 DEB
oss-linux_v4.0-1002_i386.deb

---

### Post by taurus on 2007-05-27
```
sudo dpkg -r oss-linux
sudo aptitude update
```

---

### Post by tripolitan on 2007-05-27
Pretty much the same error

root@amdsmp:/home# dpkg -r oss-linux
dpkg: error processing oss-linux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 oss-linux

---

### Post by taurus on 2007-05-27
If you still have the package, why don't you install it again and if you don't need it, remove it later.

```
sudo dpkg -i oss-linux_v4.0-1002_i386.deb
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by tripolitan on 2007-05-27
I have already tried that, dpkg will not install, un-install, purge, fix or remove.

abh@amdsmp:~/Desktop$ sudo dpkg -i oss-linux_v4.0-1002_i386.deb
Password:
Selecting previously deselected package oss-linux.
(Reading database ... 72012 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1002 (using oss-linux_v4.0-1002_i386.deb) ...
sh: /usr/lib/oss/scripts/restore_drv.sh: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
sh: /usr/lib/oss/scripts/restore_drv.sh: No such file or directory
dpkg: error processing oss-linux_v4.0-1002_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
Building OSS Modules for Linux-unknown 2.6.15-28-k7
/var/lib/dpkg/info/oss-linux.postinst: line 3: cd: /usr/lib/oss/build: No such file or directory
sh: install.sh: No such file or directory
Starting Open Sound System
touch: cannot touch `/usr/lib/oss/starting': No such file or directory
/usr/sbin/soundon: line 30: /usr/lib/oss/logs/soundon.log: No such file or directory
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: line 31: /usr/lib/oss/logs/soundon.log: No such file or directory
/usr/sbin/soundon: line 33: /usr/lib/oss/logs/soundon.log: No such file or directory
/usr/sbin/soundon: line 35: /usr/lib/oss/logs/soundon.log: No such file or directory
/usr/sbin/soundon: line 39: /usr/lib/oss/logs/soundon.log: No such file or directory
/usr/sbin/soundon: line 40: /usr/lib/oss/logs/soundon.log: No such file or directory
/usr/sbin/soundon: line 45: /usr/lib/oss/logs/soundon.log: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 oss-linux_v4.0-1002_i386.deb

---

### Post by tripolitan on 2007-05-27
I think it is choking on this package oss-linux_v4.0-1002_i386.deb

---

### Post by tripolitan on 2007-05-27
SOLVED! I found this solution here: [http://ubuntuforums.org/showthread.php?t=455541](http://ubuntuforums.org/showthread.php?t=455541)
essentially fooled synaptic/apt etc by editing /var/lib/dpkg/status by removing all references to oss-linux.

Thank you so much for taking the time to help, cheers.

---

