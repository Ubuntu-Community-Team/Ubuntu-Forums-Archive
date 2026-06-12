---
title: "Directories with bad permissions on Ubuntu 10.04 (Lucid Lynx) after fresh install"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by deere on 2010-05-21
Hi All!

I installed Ubuntu 10.04 (Lucid Lynx) Server.
After I executed "ufw enable" I got this error message:

server# ufw status
WARN: /lib/ufw is world writable!
WARN: /lib/ufw is group writable!

server# ls -lad /lib/ufw
drwxrwxrwx 2 root root 4096 2010-05-20 16:40 /lib/ufw

Then I made a try on my desktop 10.04 (also fresh install):

desktop# ls -lad /lib/ufw
drwxr-xr-x 2 root root 4096 2010-05-03 12:52 /lib/ufw

I think the permissions are only bad on server install:

server# find / -type d -perm 777
/var/log/installer
/var/lib/belocs
/boot/grub/locale
/root/.debtags
/lib/ufw
>>> these directories are installed with bad permissions


desktop# find / -type d -perm 777
>>> no result

Has someone made the same experience?

Please see my solution advice: [http://ubuntuforums.org/showthread.php?p=9337040](http://ubuntuforums.org/showthread.php?p=9337040)

---

### Post by jfine on 2011-08-04
A chmod g-w /lib/ufw was all that was needed but ya it does seem like there might be a configuration error in one of the setup packages somewhere since my install was also fresh.

---

