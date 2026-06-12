---
title: "Ubuntu 5.04 fails to install from DVD"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by Fuerte on 2005-08-14
(Sorry I somehow posted this on incorrect forum TWICE)

I have a CD-ROM drive as master and DVD-ROM drive as slave, and while the DVD boots fine from the DVD-ROM drive, when I try to install or boot "live" then it complains that it can't load from DVD or something. It also complains about MD5 failure, when I try to verify media, but at some point it says that I have the correct Ubuntu 5.04 media inserted. I have checked the DVD that it is fine, no MD5 problems.

Do I need to tell the installer somehow the correct DVD-ROM? I remember having similar problems with some other linux in the past, then I just downloaded CD-ROM images and it worked OK. Now I don't want to do it again, because I just want to try the live DVD.

---

### Post by Fuerte on 2005-08-14
More info. While the DVD md5sum.txt checks fine in Windows XP

(in fact the md5sum.txt file has bugs:

md5sum: WARNING: 31 of 4073 listed files could not be read
md5sum: WARNING: 1 of 4042 computed checksums did NOT match

that one failing file is empty)

it does not in Ubuntu installer. When I started Shell and

cd /cdrom
md5sum -c md5sum.txt

it failed about every other file. So it seems that Ubuntu installer does not support my DVD-drive, TEAC DV-W58G-A.

---

### Post by Fuerte on 2005-08-15
Now I downloaded the live CD as well, and also it has a buggy md5sum.txt:

md5sum: WARNING: 1 of 1109 listed files could not be read
md5sum: WARNING: 1 of 1108 computed checksums did NOT match

Probably it works with my CD-drive, though.

---

### Post by Fuerte on 2005-08-15
No, it didn't work. But it turns out that if I select English as language, English as location, and English as keyboard, then the files in CDROM are correct, and it works. If I select Finland as location, then it fails. The CDROM contents are decoded incorrectly and about every file is corrupt. The combination

Language: English
Location: English (or was it America)
Keyboard: Finnish

seems to work.

Someone make a bug about this?

---

