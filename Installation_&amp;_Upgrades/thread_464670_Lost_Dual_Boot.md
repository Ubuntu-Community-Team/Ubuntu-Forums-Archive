---
title: "Lost Dual Boot"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by mckinneycm on 2007-06-04
I just upgraded from 6.10 to 7.04. Before I upgraded, the boot menu had an option for Windows XP. After I upgraded, that option went away. I'm still learning Ubuntu and eventually I am going to get rid of XP. But, right now I still need to use it. How do I get that boot option back? Thanks in advance...

Also after I did the upgrade, it will no longer accept my username and password to login to Ubuntu. Is there a default username and password that it may have set it to? Or maybe a back door password?

---

### Post by confused57 on 2007-06-04
> **mckinneycm said:**
> I just upgraded from 6.10 to 7.04. Before I upgraded, the boot menu had an option for Windows XP. After I upgraded, that option went away. I'm still learning Ubuntu and eventually I am going to get rid of XP. But, right now I still need to use it. How do I get that boot option back? Thanks in advance...

Also after I did the upgrade, it will no longer accept my username and password to login to Ubuntu. Is there a default username and password that it may have set it to? Or maybe a back door password?
This might help you for your lost password:
[http://ubuntuforums.org/showthread.php?t=413308&highlight=lost+password](http://ubuntuforums.org/showthread.php?t=413308&highlight=lost+password)

Open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

There is an example of a Window's entry in your menu.lst file, if your Window's is on the first partition...your Window's entry needs to be outside the ###BEGIN AUTOMATIC KERNELS LIST & ###END DEBIAN AUTOMAGIC... lines.

---

