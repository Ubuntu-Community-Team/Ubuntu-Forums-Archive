---
title: "Triple Boot of Sorts"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by shibby4555 on 2010-12-13
So the issue at hand is:
I'm currently running a dual boot of Windows 7 and Ubuntu 10.04 on a 1TB HDD. Recently, my external hard drive power stopped working so I took the bare drive out and hooked it up directly into my motherboard. Now I have a second, unpartitioned, hard drive of 250gb. 

With that hard drive, I'd like to install Backtrack 4 onto it, unfortunately I do not have any USB drives or CDs large enough to mount the ISO.

Anybody know of any way that I could mount the Backtrack ISO directly onto that 250gb hard drive? 

Also, are there any drawbacks to triple booting?
As far as I know my computer should be able to handle it, AMD Phenom Quad Core Processor, 4gb RAM. This is kinda venturing into the unknown for me. But I really want to launch Backtrack.

Thanks in advance people,
-shibby

---

### Post by oldfred on 2010-12-14
Just be sure not to let back-tracks boot loader install to sda. I think it is still grub legacy, so install to sdv (the 250GB drive) or the partition should be ok.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

