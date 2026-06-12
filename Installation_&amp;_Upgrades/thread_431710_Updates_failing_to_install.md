---
title: "Updates failing to install"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by gewitty on 2007-05-03
Can anyone help me out on this one. After upgrading from Edgy to Feisty, I found that VirtualBox would not load any more. I checked the VirtualBox site and found that they have a new release for Feisty. I removed the original version and then tried to install the new package, but this failed. The error message is: 

**'Could not open VirtualBox_1.3.8_Ubuntu_feisty_i386.deb. The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.' **

I did a fresh download and tried again, but with the same result.

This morning, I got an update notification. When I tried to run the updates I got this message: 

[B]E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/B]

This leaves me in a no-win situation. I cannot re-install VirtualBox, but until I do, updates seem to be failing.

Can anyone give me some idea on how to resolve this (newbie language please).

---

### Post by Jussi Kukkonen on 2007-05-03
Try this on the command line and paste the output here
```
sudo apt-get remove virtualbox
```
It probably won't work right away (there seems to be a problem with virtualbox package), but maybe we'll get more information.

---

### Post by gewitty on 2007-05-03
Tried that, but got a similar error:

dave@dave-desktop:~$ sudo apt-get remove virtualbox
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

---

### Post by Jazztux on 2007-05-03
Hi, another user got the same error. Please see

[http://ubuntuforums.org/showthread.php?t=421933]("http://ubuntuforums.org/showthread.php?t=421933")

Try to follow the tutorial (I'm not sure it will work). If got an error when trying to remove the package, jump to the step 4 and try the next few passages.

Let me know if it works. ;)

---

### Post by gewitty on 2007-05-03
OK. I tried following the tutorial. The results were as follows:

dave@dave-desktop:~$ sudo bash
Password:
root@dave-desktop:~# apt-get -f remove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
root@dave-desktop:~# apt-get install gdebi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
root@dave-desktop:~# 

It seems that whatever I try, I still end up with the same error message. Is there any way to manually recreate the missing archive?

---

### Post by xtractDesigns on 2007-05-24
From terminal enter this:

sudo dpkg --remove --force-remove-reinstreq virtualbox


that'll kill it for ya and you can do a fresh install.

---

### Post by gewitty on 2007-05-24
Thanks for the info, but I already gave up and did a clean install, which cured the problem.

---

### Post by tripolitan on 2007-05-26
I've been watching this thread because I'm running into the same problem, except with a different package. I did sudo dpkg --remove --force-remove-reinstreq oss-linux and got:
```
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 72011 files and directories currently installed.)
Removing oss-linux ...
sh: /usr/lib/oss/scripts/restore_drv.sh: No such file or directory
dpkg: error processing oss-linux (--remove):
 subprocess pre-removal script returned error exit status 127
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
 oss-linux

```

I tried doing the same with any package but ended up with the same error.
I cannot see any packages in synaptic but I can with aptitude, which is failing on re-installs, installs and removals.
any thoughts?

---

### Post by tripolitan on 2007-05-27
this would have cured it too
[http://ubuntuforums.org/showthread.php?t=455541](http://ubuntuforums.org/showthread.php?t=455541)

---

