---
title: "ipmitool removal."
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by clockwork on 2006-12-04
So I am having a large problem removing a package. I need a newer version of ipmitool than what is provided by the repo's. So I have to uninstall the current version. I get the following error:

```

(Reading database ... 116541 files and directories currently installed.)
Removing ipmitool ...
 * Stopping IPMI event daemon                                            [fail] 
invoke-rc.d: initscript ipmievd, action "stop" failed.
dpkg: error processing ipmitool (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 ipmitool
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Of course if I try to install the new version from a .deb I built from a .rpm I get the following: 

```

 dpkg --install --force-all ipmitool_1.8.8-2_i386.deb 
Selecting previously deselected package ipmitool.
(Reading database ... 116542 files and directories currently installed.)
Preparing to replace ipmitool 1.8.7-2 (using ipmitool_1.8.8-2_i386.deb) ...
 * Stopping IPMI event daemon                                            [fail] 
invoke-rc.d: initscript ipmievd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing ipmitool_1.8.8-2_i386.deb (--install):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 ipmitool_1.8.8-2_i386.deb

```

Namely it appears as if the uninstall script is trying to stop a deamon that never starts, which to me is stupid. If its not running then it shouldnt care, of course the deamon doesnt have a status flag ... so yeah.

---

### Post by LLRNR on 2006-12-04
I don't know what *ipmitool* is, but I can see that when you try removing the package it fails because a certain "IPMI event daemon" cannot be stopped. 

I suppose it's a process running in the background that you can't usually see.

Try stopping it before attempting the package removal.

```
ps -e | grep ipmi
```

will give you a list of running processes that contain the string "ipmi".

If you're lucky... err... the list will not be empty and you will get at least a line that will look like

** 4356 ?        00:00:00 ipmi_something**

The first number you see on that line is the PID (the Process ID); you will try to stop this process with 

```
kill -9 4356
```

Of course, replace "4356" with the actual PID you get.

Then try removing the package again.

I hope this works.

LLRNR

---

### Post by clockwork on 2006-12-05
Actually thats the problem. the ipmievd never starts, as such when the uninstall is running the ipmievd stop command, it fails.

My respect for dpkg/apt/synaptic is going downhill quick. There should be a "shut up and do it" flag.

---

