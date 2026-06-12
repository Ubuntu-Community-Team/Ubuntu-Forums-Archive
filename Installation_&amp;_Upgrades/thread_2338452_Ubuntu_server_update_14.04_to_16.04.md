---
title: "Ubuntu server update 14.04 to 16.04"
date: 2016-09-28
forum: Installation &amp; Upgrades
---

### Post by nunor2 on 2016-09-28
Hello,

I just did a update of my ubuntu server to 16.04 (sudo apt-get dist-upgrade) but I discovered an issue when I try to install or update a package after the update

I get always the error chmod: cannot access '/sbin/udevd': No such file or directory E: Problem executing scripts DPkg: re-Invoke 'chmod -x /sbin/udevd'

```
root@braveheart:~# apt-get install php-apcuReading package lists... Done
Building dependency tree
Reading state information... Done
Recommended packages:
  php-apcu-bc
The following NEW packages will be installed:
  php-apcu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/64.0 kB of archives.
After this operation, 221 kB of additional disk space will be used.
chmod: cannot access '/sbin/udevd': No such file or directory
E: Problem executing scripts DPkg::Pre-Invoke 'chmod -x /sbin/udevd'
E: Sub-process returned an error code
root@braveheart:~#
```

I checked and /sbin/udevd is not existing. Looks like something got wrong during the update but I can't figure out out to fix this issue. 
Does anyone has an idea?

---

### Post by TheFu on 2016-09-28
**apt-get dist-upgrade** does not upgrade from release to release. It upgrades from 14.04.1 --> 14.04.2. There is a different tool to go from 14.04 --> 16.04 --> 18.04, **do-release-upgrade**. Did you run that?  Generally, it is best to run apt-get dist-upgrade a few times to get everything up-to-date, before running do-release-upgrade.

In 16.04, systemd takes over udev and stuff is different. I don't know anything about those changes, but that is where your search should begin.

---

### Post by nunor2 on 2016-09-28
Thanks for the quick answer.
For sure the server version is now 16.04. I receive this message when logging into the machine.

Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 2.6.32-042stab111.12 x86_64)

If I check /var/log/dist-upgrade/20160928-1052/main.log the only entry I can find is 
> SystemError: E Problem executing scripts DPkg: Post-Invoke 'chmod -x /sbin/udevd', E:Sub-process returned an error code

---

### Post by TheFu on 2016-09-28
2.6.32-042stab111.12 x86_64 - doesn't make sense.

**uname -a**?

You've got some weirdness happening. The 2.6 kernels haven't been used in .... years - like 5 yrs.  A properly maintained 16.04.1 system should have 4.4.0-38 kernel version. A properly maintained 14.04.5 server should have 3.13.0-96 kernels.

Time to flush it completely and start over
  or
restore from the backup prior to the last migration attempt and see if the migration can happen with better results ... like getting a current kernel.

Assuming I'm reading that output correctly.

---

### Post by 8-uduntu-e on 2016-12-10
I have exactly the same problem...
Is your server hosted in OVH ?

Looking on the root of the filesystem I don't see any kernel :o and also the /boot directory is empty...
btw, I used do-release-upgrade.

uname -a
Linux XXXX 2.6.32-042stab111.12 #1 SMP Thu Sep 17 11:38:20 MSK 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by 8-uduntu-e on 2016-12-10
Digging around I found this post:

[http://askubuntu.com/questions/713746/cannot-access-sbin-udevd-no-such-file-or-directory](http://askubuntu.com/questions/713746/cannot-access-sbin-udevd-no-such-file-or-directory)

The command **touch /sbin/udevd** solved my problem.

---

