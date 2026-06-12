---
title: "ddrescue and foreign language filenames"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by mr_mop on 2012-10-24
I am trying to take a ddrescue copy of a partition prior to an update, but it is losing all of the Japanese filenames.

I have Japanese filenames as I have some Japanese music CDs which I have ripped and kept the Japanese track names.

Is there a way to correctly copy these file names with ddrescue?

The command I am using is:
sudo ddrescue --no-split /dev/<partition> <image> <logfile>

Thanks

MM

---

### Post by TheFu on 2012-10-24
I haven't used ddrescue with UTF8 filenames, but are you certain that both file systems are setup to support utf8 filenames?

It is possible that ddrescue was not coded to support anything except ASCII filenames. In theory, it may be possible to find that code and change it, but that is completely dependent on your skill.

---

### Post by mr_mop on 2012-10-25
Ah, could that be my problem?  I did not use iocharset=utf8 when mounting the image file.  I'll try that and see if that makes a difference.

---

### Post by mr_mop on 2012-10-25
Yes, that did the trick.  Adding the option to make the command line:

sudo mount -o loop,iocharset=utf8 /media/D\ DRIVE/banbaPC.img ~/mnt

allowed this to work.

:guitar:

---

