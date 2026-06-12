---
title: "upgrade aborted"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by louis.roux on 2010-11-27
I spent the past several hours upgrading from 10.04 to 10.10 but near the end I got a box that said the upgrade has been aborted and in the box it had the following information:

Failed to fetch cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/l/lupin/lupin-support_0.32_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.4-14ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/g/gcc-4.4/g++-4.4_4.4.4-14ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/g/gcc-defaults/g++_4.4.4-1ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-1_all.deb Hash Sum mismatch

What now????

---

### Post by Hippytaff on 2010-11-27
Did you upgrade from disc or update manager or from a terminal?

Looks as though there was an MD5SUM problem!? maybe :-)

---

### Post by louis.roux on 2010-11-27
not sure.  I started through the update manager but it had me put the disk in about half way through.  I never had that problem with the last two upgrades.  Never asked for the disk.  Sooooo confused.

---

### Post by Hippytaff on 2010-11-27
That is odd...so your not able to boot 10.10, can you get as far as being able to choose recovery mode? if so drop into a terminal with networking and try
```

sudo apt-get update && sudo apt-get upgrade

```
and 
```

sudo apt-get dist-upgrade

```
and if you can report any errors you get...

btw do you have a seperate /home partition? - might be worth doing a livecd install :-)

---

