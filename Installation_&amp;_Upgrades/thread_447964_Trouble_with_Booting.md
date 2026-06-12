---
title: "Trouble with Booting"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by a1tone on 2007-05-18
I have just received a Ubuntu CD directly from Ubuntu. I have installed on my PC and was ready to start exploring, but....

Upon reboot, I get the following error.

GRUB Loading stage1.5. 

GRUB loading, please wait... 

Error 2

Then the boot-up sequence stops.

Anyone have  any ideas.

Thanks

---

### Post by Cappy on 2007-05-18
I think you should follow this guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by a1tone on 2007-05-18
I have tried that and still the same happens.

---

### Post by a1tone on 2007-05-19
Hi

I have tried a full re-installation today, but still the same happens. I tried the guide suggested above, but still nothing. The same error keeps appearing.

Any ideas???

---

### Post by Cappy on 2007-05-19
Does it work when you have the Live CD in and use "boot from first disk"?

I found the bug report for this, maybe you can give them some information, it seems be a relatively new bug:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/17635](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/17635)

This thread suggests it is a corrupted partition or hardware related.
[http://www.linuxquestions.org/questions/showthread.php?t=352343](http://www.linuxquestions.org/questions/showthread.php?t=352343)

Someone else here at this problem a couple of days ago, they didn't find a solution:
[http://www.linuxquestions.org/questions/showthread.php?p=2751678](http://www.linuxquestions.org/questions/showthread.php?p=2751678)

There isn't very much information on this problem =(

What kind of partitioning are you using when you install Ubuntu? Do you use the whole disk? Are you using a logical or an extended partition for Ubuntu? Ubuntu might need to be installed on the first partition on the disk.

In one of the other threads someone said that another linux distro worked fine without this problem.

---

### Post by vpjr on 2007-05-19
deleted a mistake

---

### Post by vpjr on 2007-05-19
deleted a mistake

---

