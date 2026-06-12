---
title: "Kernel panic - not syncing / relocation error / libc.so.6"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by thync on 2010-04-15
I've scoured several forums for days now and have yet to find a solution to my particular problem, although several problems have been similar (e.g. [http://ubuntuforums.org/showthread.php?t=1324375](http://ubuntuforums.org/showthread.php?t=1324375)).

A bug has also been posted but has yet to be assigned:
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/486576](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/486576)

I tried to upgrade Empathy from 2.28 to 2.30 via Synaptic but the upgrade always failed as there were some errors to do with the dependencies (libglib2.0* and others). The dependency issues were odd as it told me that Empathy wanted to install files that were older than the existing ones. So I decided to uninstall Empathy and all its dependencies, and re-install the whole (updated) package and it's dependencies from scratch via Synaptic. After the install, Ubuntu told me that there were broken packages and Update Manager kept on popping up asking me to run a partial upgrade to fix these broken packages. Well, the partial upgrade also failed (due to the same dependency issues , I suspect) so I decided that I'll run a full system update (as Update Manager had being bugging me prior to my failed Empathy upgrade). 486 Mb later, Ubuntu no longer wants to boot - it freezes on the splash screen.

When I start it in recovery mode, it spews out the various processes being loaded. However, it eventually freezes with the following on screen:[INDENT]/sbin/init: relocation error: /sbin/init: symbol __abort.msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference

[    8.936454] kernel panic - not syncing: Attempted to kill init!

Pid: 1, comm: init not tainted 2.6.31-20-gen #58 Ubuntu
[/INDENT]Trying to run earlier kernels (2.6.31-19 / 17 / 14) from GRUB, in both normal mode and recovery mode does not seem to help.

I am running Ubuntu 9.10, kernel 2.6.31-20-generic.

a) Is the problem to do with the kernel - did the update try to update the kernel as I note that there is a new stable release (2.6.33-2)? However, GRUB still indicates that the kernel is 2.6.31-20.

b) Would updating the kernel to 2.6.33-2 help? If so, how do I do this? 

c) Is the problem, as I suspect, to do with the libglib* files? If so, how do I fix it?

I can only run Ubuntu from a LiveUSB/CD device. I can also load PMagic (which contains SuperGRUB 2) from USB if that offers any help.

P.S.: I am a fairly new user so be gentle.

Many thanks in advance
Perplexed

---

### Post by thync on 2010-04-20
*bump*

---

### Post by Sepiraph on 2010-05-26
Heh, I have the same problem ERROR ```
/sbin/init: relocation error: /sbin/init: symbol __abort.msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
```after doing a partial upgrade on 9.10 (typing this from a Vista ...)

The other thread [http://ubuntuforums.org/showthread.php?t=1324375](http://ubuntuforums.org/showthread.php?t=1324375) had similar

Anyway, I did a bit of googling and this is what I found so far...

[http://mandrivausers.org/index.php?/topic/38316-libc-so-6-problems/?](http://mandrivausers.org/index.php?/topic/38316-libc-so-6-problems/?)

[http://www.howtoforge.com/forums/showthread.php?t=446](http://www.howtoforge.com/forums/showthread.php?t=446)

Those issues are not at bootup, but after upgrading specific program and starting them where they got similar issue.  They fixed it by editing the version that LD_ASSUME_KERNEL points to.  So my question would be if there is also a file that the bootup process uses that has this parameter?

---

