---
title: "Upgrading the kernel to 3.7"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by IReadTheManual on 2013-02-18
I want to make sure that I upgrade the kernel to 3.7 in the correct way, and that I still have the option to select all previous kernels during boot as I can currently. I do not necessarily want it to be my default kernel either, but I need to use some new hardware drivers which were added, every now and then.

I have a laptop which is running Ubuntu 12.10 (upgraded from the original install of 12.04)
```
Linux version 3.5.0-24-generic (buildd@akateko) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #37-Ubuntu SMP Thu Feb 7 05:32:22 UTC 2013
```

I found this: [http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade) , but I am not sure if this is the correct way and what the differences would be to make sure that I get 3.7.

A search on this forum  of `upgrade kernel "3.7" ` results `Sorry - no matches. Please try some different terms.  `, although this may be because of the updating from vB3 to vB4 this forum currently undergoing.

---

### Post by Kow on 2013-02-18
Check this out:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

Check this out for changing the default kernel to boot in Grub2:
[https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)

---

### Post by UltimateCat on 2013-02-18
Here's the latest stable kernel:;) 3.7.9 

[http://www.kernel.org/](http://www.kernel.org/)

[http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

Sometimes when you upgrade to a new kernel you will have to re-install a driver-
Just so you'll know-

Fedora that I am currently running is using the 3.7.3 kernel and I haven't had any problems.

Hope this helps

---

