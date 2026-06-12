---
title: "/boot folder full, which to remove, how to maximize space"
date: 2015-12-13
forum: Installation &amp; Upgrades
---

### Post by anotherusername2 on 2015-12-13
I have been trying to update but my /boot folder seems to be full again. I had posted once about this [here]("http://ubuntuforums.org/showthread.php?t=2303580"), thinking it was a one-time thing, but I have the same problem again. To avoid the inconvenience of (probably) having this problem from time to time, is it OK if I remove the three or four oldest kernels? (I'm a beginner, so I'm just basing this on the solutions given to me in the other thread.) Is it safe to take out as many as you can?

me@me-PORTEGE-M600:~$ sudo apt-get autoremove
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
me@me-PORTEGE-M600:~$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       236M  158M   67M  71% /boot
me@me-PORTEGE-M600:~$ ls -lhA /boot
total 149M
-rw-r--r-- 1 root root 1.2M Sep  9 19:36 abi-3.16.0-49-generic
-rw-r--r-- 1 root root 1.2M Oct  3 08:19 abi-3.16.0-50-generic
-rw-r--r-- 1 root root 1.2M Oct  8 00:58 abi-3.16.0-51-generic
-rw-r--r-- 1 root root 1.2M Nov  7 04:36 abi-3.16.0-53-generic
-rw-r--r-- 1 root root 173K Sep  9 19:36 config-3.16.0-49-generic
-rw-r--r-- 1 root root 173K Oct  3 08:19 config-3.16.0-50-generic
-rw-r--r-- 1 root root 173K Oct  8 00:58 config-3.16.0-51-generic
-rw-r--r-- 1 root root 173K Nov  7 04:36 config-3.16.0-53-generic
drwxr-xr-x 5 root root 1.0K Nov 21 10:26 grub
-rw-r--r-- 1 root root  28M Sep 28 17:10 initrd.img-3.16.0-49-generic
-rw-r--r-- 1 root root  28M Oct 17 07:39 initrd.img-3.16.0-50-generic
-rw-r--r-- 1 root root  28M Oct 24 09:12 initrd.img-3.16.0-51-generic
-rw-r--r-- 1 root root  28M Nov 21 10:26 initrd.img-3.16.0-53-generic
drwx------ 2 root root  12K Sep 28 02:00 lost+found
-rw-r--r-- 1 root root 173K Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root 174K Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root 175K Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root 2.7M Sep  9 19:36 System.map-3.16.0-49-generic
-rw------- 1 root root 2.7M Oct  3 08:19 System.map-3.16.0-50-generic
-rw------- 1 root root 2.7M Oct  8 00:58 System.map-3.16.0-51-generic
-rw------- 1 root root 2.7M Nov  7 04:36 System.map-3.16.0-53-generic
-rw------- 1 root root 5.8M Sep  9 19:36 vmlinuz-3.16.0-49-generic
-rw------- 1 root root 5.8M Oct  3 08:19 vmlinuz-3.16.0-50-generic
-rw------- 1 root root 5.8M Oct  8 00:58 vmlinuz-3.16.0-51-generic
-rw------- 1 root root 5.8M Nov  7 04:36 vmlinuz-3.16.0-53-generic

---

### Post by ian-weisser on 2015-12-13
> **anotherusername2 said:**
> is it OK if I remove the three or four oldest kernels?
[...]
Is it safe to take out as many as you can?
No. It's possible to remove too many and leave your system unbootable.
Use the 'uname' command to determine your curently running kernel. Do not remove it under any circumstances.
Most old-timers here quite rightly recommend leaving one older kernel as well, to ensure a recovery option if the current kernel fails.

Running autoremove generally does not work when you run out of space. Apt will try to install packages awaiting installation first, which fails becasue of the lack of space. 
You must schedule and run autoremove regularly *before* you run out of space.

Ubuntu marks older kernels as *eligible* for autoremoval, but does not actually do the autoremoval by default.
You can configure the 'unattended-upgrades' to do all the maintenance automatically every day (my preferred solution), or you can do so manually anytime you wish...except when you're out of space and have packages awaiting install.

---

### Post by anotherusername2 on 2015-12-17
> **ian-weisser said:**
> You must schedule and run autoremove regularly *before* you run out of space.
...
You can configure the 'unattended-upgrades' to do all the maintenance  automatically every day (my preferred solution)...

Thanks. How do I do those?

---

### Post by grahammechanical on 2015-12-17
You actually only have 4 kernels. 3.16.0-49: 3.16.0-50; 3.16.0-51; 3.16.0-53. What we call a "kernel" is actually a small set of kernel related files. And the ones you should keep are 3.16.0-53 & 3.16.0-51. They are the 2 latest kernels.Check that they both load to a working desktop. 

We do that by selecting Advanced options for Ubuntu at the Grub boot menu. The first kernel on the list should be the default kernel (which should be 3.16.0-53). But you will see the other kernels listed and we can select them also if we need to. You will also see kernels with recovery mode as an option. It is still the same number of kernels but with different boot parameters.

Selecting recovery mode will bring up a menu that has an option called "clean - try to make free space." That will run both apt-get autoremove and apt-get clean. That might get you somewhere.

This shows us how to remove specific kernels when at the desktop & using the terminal.

[URL="https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels"]https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels

[/URL]Regards

---

