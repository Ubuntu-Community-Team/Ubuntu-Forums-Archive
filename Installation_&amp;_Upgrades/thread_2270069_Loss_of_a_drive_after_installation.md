---
title: "Loss of a drive after installation"
date: 2015-03-20
forum: Installation &amp; Upgrades
---

### Post by nikunj3 on 2015-03-20
HI guys,

I have recently installed ubuntu in my system. During the installation I had selected the option where in i replaced my Windows 7 OS. I thought that only C drive would be replaced. But now when i logged in i found my system  entirely wiped to new brand HD. Please suggest if i can recover my lost data which was packed in Drive D. Thanks

---

### Post by v3.xx on 2015-03-20
The only thing I know of is TestDisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by haiko22012 on 2015-03-20
check in the terminal

sudo fdisk -l

maybe your "D" is just not mounted ;)

---

### Post by Impavidus on 2015-03-20
It told you it would wipe the drive, which indeed means the entire drive. The fact that Windows calls a partition a drive too doesn't help of course...

Don't write anything to the hard drive until you either cloned it to a different drive or exhausted all possibilities for file recovery. And that includes mounting it read-write and just reading files, as that will already write some metadata. You may be able to recover quite some files, but probably not everything. I've never used file recovery tools myself, so I can't help you further.

---

### Post by Mark Phelps on 2015-03-20
Your best bet, if Testdisk doesn't restore the entire partition, is to use Windows data recovery apps.  And, to do that, you would need to be able to remove the drive and attach it to a working Windows PC.

IF you can do that, then do the following:
1) Connect the drive to the working Windows PC
2) Boot the Windows PC
3) Download and install "recuva" This is a free Windows data recovery app
4) Run recuva and select Partition Recovery
5) If that works, then you should check the partition to see if the files and folders you need are OK
6) If that doesn't work, then try Lost File Recovery.
7) If that works, then you should check to see ifn the files and folders you need are OK
8) If that doesn't work, then download and install RecoverMyFiles.  This is free to download and try out.
9) Run that in deepest discovery mode -- probably overnight
10) If that finds the files and folders you want, you will need to go online and purchase a license to do the actual data recovery.

Good Luck

---

