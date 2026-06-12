---
title: "Any upgrade from 9.10 to 8.04 LTS success story ?"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-03-24
Has any body upgraded from 9.10 to 8.04 LTS  on laptop successfully ?
it destroy my installation, but that was wubi installation.

---

### Post by jorj82 on 2010-03-24
9.10 to 8.04?  That's not an upgrade ;)  If you meant 8.04 to 9.10, you have to upgrade one version at a time: 8.04 to 8.10 to 9.04 to 9.10.  It would probably be quicker and simpler just to get the 9.10 Live CD (download iso and burn), back up your files, and do a fresh install.

Hope that helps :)

---

### Post by slakkie on 2010-03-24
8.04 to 9.10 is possible for KDE users.

I've done it with success during the alpha/beta phase of Karmic.

---

### Post by pmlxuser on 2010-03-24
you can do it with the alternative cd .. it does wonders, you would do it from any version i guess... and with no internet at all.

challenges is you still have to connect to internet and do the updates...

---

### Post by phillw on 2010-03-24
Hi,

If you're going to upgrade 8.04 LTS, why not wait a few weeks and do the 8.04 LTS --> 10.04 LTS upgrade ?

Get your 8.04 to 8.04.4 in readiness, the 8.04 --> 10.04 is being tested at present.

[http://ubuntuforums.org/showthread.php?p=8740883](http://ubuntuforums.org/showthread.php?p=8740883)

Do note, that you will still be on ext3 (and possibly grub legacy).

As it is a non too common upgrade (every two years) you may want to make a separate /home (if you don't already have one) and do a clean install of 10.04 [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

A note of caution, if you do make a separate /home and want ext4 (the default File System) You'll need to upgrade grub legacy to the new grub. [https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading) to GRUB 2


Regards,

Phill.

---

