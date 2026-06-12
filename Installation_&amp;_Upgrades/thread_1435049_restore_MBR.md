---
title: "restore MBR"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by mr.g on 2010-03-21
Dear Forum Members,

I have an old old IDE hard disk which contains a lot of important data and applications.  It was taken from my previous computer.  Now I installed it on my new computer so I can run the application I used to run.

Unfortunately I found the HD is not boot-able anymore.  However, when I boot the computer with a live CD I do find the content actually readable.  Is there any way to repair the MBR of a hard disk?

G

---

### Post by dineshs on 2010-03-21
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by mr.g on 2010-03-21
Hi,

I tried almost all the methods, but they does not seem to work.
When I tried "grub", the system tells me that I don't have grub installed.

Later, I tried:
*****
mkdir /ubuntu
mount /dev/sda /ubuntu
*****
the system returns:
*****
/dev/sda already mounted or /ubuntu busy
*****
then i typed:
*****
grub-install /dev/sda
*****
the system returns:
*****
/usr/sbin/grub-probe:  error:  cannot find a device for /boot/grub (is /dev mounted?)
*****

I did not really tried the install-withdraw method as it seems to risky for me. (the disk contains very important data)  i did try up to the point that installer warn me the data might be deleted.

What should I do now?

G

P.S. The hard disk is a IDE hard disk.

---

