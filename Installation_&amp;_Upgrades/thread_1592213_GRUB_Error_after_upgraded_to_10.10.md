---
title: "GRUB Error after upgraded to 10.10"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-10-10
I used wubi to install the dual booting, after I have upgrade from 10.04 to 10.10 when I launch linux it goes direct to grup.
what can I do ?

---

### Post by kansasnoob on 2010-10-10
Ouch, should have read the release notes first:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

> #

The Wubi Windows installer was reported to be unable to open Windows' boot configuration data store in some (but not all) cases. Investigation of the problems are ongoing (613288)
#

You cannot upgrade if wubi is installed to a partition other than Windows. (610898,653134) 

---

### Post by hoboy on 2010-10-10
> **kansasnoob said:**
> Ouch, should have read the release notes first:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

I am using windows 7

---

### Post by bcbc on 2010-10-10
What partition is ubuntu installed to? e.g. 

e.g. if it's on /dev/sda2 you can run: 
configfile (hd0,2)/ubuntu/winboot/wubildr.cfg

Otherwise run "ls" (lowercase LS) to see available partitions and try all of the ones in the form (hd0,Y) in the above command.

Still not guaranteed to work due to the other big wubi bug. If that fails, you'll have to loopmount the root.disk and edit grub.cfg as described here [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by dino99 on 2010-10-10
if you want something serious, kick off wubi and make a real install

---

