---
title: "damaged /etc/mtab file"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Crasch on 2010-05-11
I installed ubuntu 10.4 on a 8G pen drive.
Everithing went smooth, after doing some stuff (updgading, mounting samba) I get a damaged mtab file.
No matter what I try this file seems to be gone. (sudo gedit /etc/mtab, sudo rm /etc/mtab )

doing a ls -l I get

lrwxrwxrwx  1 root    root       13 2010-04-29 12:17 motd -> /var/run/motd
-?????????  ? ?       ?           ?                ? mtab
-rw-r--r--  1 root    root      624 2009-11-13 18:45 mtools.conf

Trying to mount a drive I get

Error mounting: mount exited with exit code 21: mount: according to mtab, /dev/sdb1 is already mounted on /media/System

Obviously I found nothing on /media.

Any idea on how solve this problem?

---

