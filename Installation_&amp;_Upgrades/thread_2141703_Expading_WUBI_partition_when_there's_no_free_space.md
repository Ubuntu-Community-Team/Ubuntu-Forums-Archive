---
title: "Expading WUBI partition when there's no free space"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by dankki on 2013-05-03
Hey.

I have a 18Gb installation with WUBI, it's currently full and I'm trying to expand it. I tried with this: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk) but it wont let me expand it because the current partition doesn't fit a copy of the root.disk. Would it be possible to move the root.disksomewhere there is empty space and expand it there? (I'm terrible with shell scripts, I did a bit of poking around but no success.) I have other partitions which have plenty of space. Also, I tried converting it to a normal partition, but my Live CD is a 32-bit, so it can't convert it because the installation itself is 64-bit.

I'm using Ubuntu 12.10.

Thanks!

---

### Post by oldfred on 2013-05-03
Maybe time to download the 64 bit version so you can convert?

 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

      
 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

      
 Resize wubi - bcbc
[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by dankki on 2013-05-03
Thanks.

Yea, might be a better idea to download the 64-bit. Also, would it be better to re-install a fresh installation without WUBI, or does it make any big difference after converting it to a dedicated partition?

---

### Post by oldfred on 2013-05-03
I do not know details of conversion script.

But I tend to prefer clean installs. You then get an auto houseclean of log files and old cruft.
But if you have installed a lot of applications you should make a list with dpkg and if you have customized and saved data in /home you should make a full backup of /home and/or copy /home to a separate partition to preserve your data & settings and use that partition as part of  your install.

This is what I backup so I can do a clean install or install a new version.
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

But I usually install to a new / (root) partition so I can go back and find something I missed if necessary. If you have space do not delete wubi until after you have new install working the way you want. I normally suggest 10 to 25GB for / (root) and 2GB for swap and then the rest of the space you want to allocate to Ubuntu for /home. If total space is 30GB or less then do not make a separate /home but leave it in /.

---

### Post by bcbc on 2013-05-03
There is also this option [https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk) which can be done from a live CD and is a true resize.

In terms of migrating or installing fresh, migrating will keep your current settings/data/programs in place. So it depends on how much effort it would be to redo that. Note that you don't have to migrate from a live CD - it's preferred to do it from the Wubi install. Only if you are replacing the partition that the Wubi install is currently on, in which case a live CD would be required.

---

### Post by dankki on 2013-05-05
Thanks for the links, olfred. I  installed the 64-bit and without a problem moved it to it's own partition. Cheers.

---

### Post by oldfred on 2013-05-05
Glad that worked. :)

---

