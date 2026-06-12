---
title: "Can't install a package - Permissions error while using sudo"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by Spaceman Spiff on 2010-03-17
Hey gentleman(and ladies),

tl;dr - sudo make -> operation not permitted, sudo chown -R 777 * -> operation not permitted on some of the files 

--------------------

I am trying to install a library and am having some confusing/frustrating issues.  The biggest issue is permissions, if we could tackle this issue I am sure I can figure out the others...

The problem:
 Sudo make is getting permission denied on file 1, while using regular make I am getting permission denied on file 2.  I have noticed some of the directories in the library are under nobody:nogroup.  I tried chown and sudo chown, both didn't work.  Sudo chown got permission errors, while chown didn't change ALL the files. (operation not permitted once again)  Tried sudo su, and working from there, that also did not work. (permission once again).  Using lsattr returned "lsattr: Inappropriate ioctl for device While reading flags on".

```
sudo chmod -R 777 *
chmod: changing permissions of `Makefile': Operation not permitted
chmod: changing permissions of `Makefile.am': Operation not permitted
chmod: changing permissions of `Makefile.in': Operation not permitted
chmod: changing permissions of `queue.c': Operation not permitted
chmod: changing permissions of `queue.h': Operation not permitted
chmod: changing permissions of `ucutil.h': Operation not permitted

```

Note the .libs folder not having write permission....
```
chmod -R 777 *
constantin@Nadfadfo:~/network_home/constantin/libraries/unicap/libunicap-0.9.8/common$ ls -la
total 68
drwxrwxrwx 4 constantin constantin  4096 2010-03-17 11:31 .
drwxrwxrwx 8 constantin constantin  4096 2010-03-17 11:31 ..
drwxrwxrwx 2 constantin constantin  4096 2010-03-17 11:31 .deps
drwxr-xr-x 2 nobody       nogroup       4096 2010-03-17 11:31 .libs
-rwxrwxrwx 1 constantin constantin 15295 2010-03-17 11:31 Makefile
-rwxrwxrwx 1 constantin constantin   130 2010-01-17 08:17 Makefile.am
-rwxrwxrwx 1 constantin constantin 15262 2010-01-17 08:17 Makefile.in
-rwxrwxrwx 1 constantin constantin  6101 2010-01-17 02:49 queue.c
-rwxrwxrwx 1 constantin constantin  1667 2010-01-17 02:49 queue.h
-rwxrwxrwx 1 constantin constantin   125 2010-01-17 02:49 ucutil.h


```

System: Karmic Koala 64-bit

Any help would be appreciated.  Thank you.
------------

---

### Post by thefallofroy on 2010-03-17
I had a problem with sudo when I was installing Java for the first time. Maybe try resetting the password. I forget how, hopefully you know, if not I'm sure someone else will be able to help.

---

