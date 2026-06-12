---
title: "can't  remove dell provided .deb file"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by Phantom784 on 2008-05-09
In an attempt to get sound recording to work, I installed  a .deb file provided at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work) .  It didn't  fix the problem, and I later  got sound  recording working with another technique.  However, I am now getting an error about the package system being broken,  and I would  like to remove this package.  When I try to remove it in Synaptic, I get the following error ```
E: linux-backports-modules-2.6.22-14-generic: subprocess post-removal script returned error exit status 1
```

and the following is shown under "details" ```
dpkg: status database area is locked by another process
francis@plutonium:~$ sudo dpkg --remove linux-backports-modules-2.6.22-14-generic 
(Reading database ... 122799 files and directories currently installed.)
Removing linux-backports-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-backports-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.22-14-generic

```

Edit:  It looks like the problem is that the .deb was written for the 2.6.22.14 kernel, while  i have 2.6.24.16 (and I never  should have installed it in the first place).  Still, how do I get rid of it?

---

### Post by Partyboi2 on 2008-05-10
looks like someone else had a similar problem, they fixed it by removing any reference to   linux-backports-modules-2.6.22-14-generic from /var/lib/dpkg/status
([http://ubuntuforums.org/showthread.php?p=4861243](http://ubuntuforums.org/showthread.php?p=4861243))

---

