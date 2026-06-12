---
title: "Installation of Ubuntu 12 doesn't boot"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by Cancellator on 2012-05-05
Hi,

I installed Ubuntu on the same hard drive as my Windows 7 installation, on different partitions. However, when selecting where to "install boot menu entry", I foolishly picked the same partition as the Ubuntu install, instead of the entire hard drive.

As a result, the PC boots straight into Windows. Is there any way to fix this, or will I have to format the Ubuntu partition from Windows and do the whole process again?

Thanks

PS: Because I already had 3 partitions (from the recovery programs pre-installed on my laptop), I could not make a 5th partition for swap. Will this come and haunt me at some point, or is it ok? ( I installed Ubuntu 64 bit on a 8 GB ram machine ).

---

### Post by darkod on 2012-05-05
No, you don't have to format or reinstall.

And you could have created root and swap as logical partitions, in that case they are part of a single extended partition and you are still within the limit with 3 primary + 1 extended. With 8GB ram you would barely use swap anyway.

To reinstall grub2 to the MBR you can use this from live mode:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

