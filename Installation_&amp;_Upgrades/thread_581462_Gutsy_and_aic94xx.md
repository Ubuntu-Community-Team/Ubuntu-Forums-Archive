---
title: "Gutsy and aic94xx"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by nshopik on 2007-10-19
Hi everyone,
I've just tried to install gutsy on one of my server with adaptec aic-9410 but installer won't detect any hard drives. I tried to select manually aic94xx driver on select driver screen but it doesn't help.
Any ideas what's wrong here?

---

### Post by nshopik on 2008-01-23
Well its seems it depends on external firmware which is not in place /lib/firmware. you need to download it from here
[http://kernel.org/pub/linux/kernel/people/jejb/aic94xx-seq.fw](http://kernel.org/pub/linux/kernel/people/jejb/aic94xx-seq.fw) and copy to /lib/firmware when you in installer.

original message from here 
[http://lists.debian.org/debian-kernel/2007/01/msg00787.html](http://lists.debian.org/debian-kernel/2007/01/msg00787.html)

---

### Post by nshopik on 2008-01-30
latest version of firmware available at Adaptec site. (u need to unpack RPM file to get firmware)
[http://www.adaptec.com/en-US/speed/scsi/linux/aic94xx-seq-30-1_tar_gz.htm](http://www.adaptec.com/en-US/speed/scsi/linux/aic94xx-seq-30-1_tar_gz.htm)

---

