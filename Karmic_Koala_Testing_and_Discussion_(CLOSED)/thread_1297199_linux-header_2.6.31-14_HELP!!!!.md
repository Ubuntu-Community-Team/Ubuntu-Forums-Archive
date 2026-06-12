---
title: "linux-header 2.6.31-14 HELP!!!!"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by KegHead on 2009-10-21
Hi

I need help updating the following.

Thanks!

KegHead

jim@jim-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-headers-2.6.31-14
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/9,526kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 208263 files and directories currently installed.)
Preparing to replace linux-headers-2.6.31-14 2.6.31-14.47 (using .../linux-headers-2.6.31-14_2.6.31-14.48_all.deb) ...
Unpacking replacement linux-headers-2.6.31-14 ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.31-14_2.6.31-14.48_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-2.6.31-14/include/sound/Kbuild.dpkg-new' (while processing `./usr/src/linux-headers-2.6.31-14/include/sound/Kbuild'): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.31-14_2.6.31-14.48_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@jim-laptop:~$

---

### Post by ikisham on 2009-10-21
People more knowledgeable than me may give you a simpler solution to this (maybe it's only something that messed the update/dpkg mechanism and not the linux-headers package itself). But one (maybe overkill) way to clean this would be you boot to a former kernel (2.6.31-13), use the computer janitor to clean the 2.6.31-14 kernel, make sure all is ok and then upgrade again.

---

### Post by ranch hand on 2009-10-21
Have you tried running;
```

sudo dpkg --configure -a

```
and what did that have to say?

---

### Post by xebian on 2009-10-21
> **KegHead said:**
> Hi

..
 unable to create `/usr/src/linux-headers-2.6.31-14/include/sound/Kbuild.dpkg-new' (while processing `./usr/src/linux-headers-2.6.31-14/include/sound/Kbuild'): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.31-14_2.6.31-14.48_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@jim-laptop:~$

Looks like you are running out of space.

---

