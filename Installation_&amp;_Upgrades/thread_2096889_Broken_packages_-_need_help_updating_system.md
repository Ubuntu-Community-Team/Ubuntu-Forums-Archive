---
title: "Broken packages - need help updating system"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by Ken Kaniff on 2012-12-21
Hi all,

I'm running Xubuntu 12.04. Yesterday the Update Manger showed new updates but I can't seem to be able to run them. There are two items that I'm unsuccessful with:

- header files related to kernel version 3.2.0. (new install)
- linux kernel headers version 3.2.0.  (new install)

I keep getting the following error messages:

```
E: /var/cache/apt/archives/linux-headers-3.2.0-35_3.2.0-35.55_all.deb: unable to create `/usr/src/linux-headers-3.2.0-35/arch/sparc/include/asm/checksum_32.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-35/arch/sparc/include/asm/checksum_32.h'): No space left on device

E: /var/cache/apt/archives/linux-headers-3.2.0-35-generic_3.2.0-35.55_i386.deb: error creating directory `./usr/src/linux-headers-3.2.0-35-generic/include/config/line6': No space left on device
```

I do, however, have space in the home directory. See the graph:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=228959&stc=1&d=1356097424[/IMG]


What should I do about the warning messages? Any idea is welcome. Thanks.

---

### Post by Pjotr123 on 2012-12-21
No space left. Throw away some stuff or enlarge your partition.

Better still: start anew, and don't create a separate /home, because that's in my opinion not useful anyway:
[https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-](https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-)
(item 15, right column)

---

### Post by Ken Kaniff on 2012-12-21
Pjotr123, thanks. Not sure about installing the system from scratch right now. Looks like I will have to do that at some point anyway.

What do you suggest I can safely get rid of to make some space?

---

### Post by bazsound on 2012-12-21
If you have downloaded alot of updates or installed a lot of packages, there may be a tone of cached packages taking up disk space try

```
sudo apt-get clean
apt-get autoclean
```

this should clear your cache of downloaded packages which resides on your root partation.

8gb isnt really big enough for a root partation imo.


You could merge your root partition and your home partition, however do not try any messing with partitions unless you know what your doing. ive  never tried this and i dont know if it may mess up your installation. the other option being taking some space from your home partition.

tbh it would be much easier to backup any files you need and reinstall ubuntu. it only takes 40 minutes.

I used to partition my ubuntu with the idea of keeping my home directory if something went wrong. but with live cd's and being able to chroot into a broken installation. doesnt really seem nessesary since you can just boot into a live cd and save anything you need or try and rescue the system.

---

### Post by Ken Kaniff on 2012-12-21
> **bazsound said:**
> If you have downloaded alot of updates or installed a lot of packages, there may be a tone of cached packages taking up disk space try

```
sudo apt-get clean
apt-get autoclean
```


this should clear your cache of downloaded packages which resides on your root partation.



Good advice that freed up approximately 300MB of disk space.
> **bazsound said:**
> 

8gb isnt really big enough for a root partation imo.


You could merge your root partition and your home partition, however do not try any messing with partitions unless you know what your doing. ive  never tried this and i dont know if it may mess up your installation. the other option being taking some space from your home partition.

I'm not an expert user and I've had a fair share of messed up installations, so I won't try merging.

> **bazsound said:**
> 

tbh it would be much easier to backup any files you need and reinstall ubuntu. it only takes 40 minutes.

I used to partition my ubuntu with the idea of keeping my home directory if something went wrong. but with live cd's and being able to chroot into a broken installation. doesnt really seem nessesary since you can just boot into a live cd and save anything you need or try and rescue the system.

Guess, you got me convinced. And with a tiny HD running dual boot I may get rid of my other system, which I hardly ever need to access anymore.

Thanks again, I appreciate the help.

---

### Post by Bashing-om on 2012-12-21
Ken Kaniff;
'Nother place to get some head room, delete the archived log files in the various directories in /var/log; Any file ending in ".gz" may be safely deleted.

[INDENT]just my 2 pounds worth <== BDQ

[/INDENT]

---

### Post by Ken Kaniff on 2012-12-22
> **Bashing-om said:**
> Ken Kaniff;
'Nother place to get some head room, delete the archived log files in the various directories in /var/log; Any file ending in ".gz" may be safely deleted.

[INDENT]just my 2 pounds worth <== BDQ

[/INDENT]

Hi, appreciate the comment. I've found some .gz files, though they didn't amount to much. Decided to do a fresh install--I'm downloading a 12.04 xubuntu torrent right now.

---

