---
title: "Fat 32 USB drives"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by unclesirbobby on 2008-09-27
I am after a version of Ubuntu that can read USB drives automatically. I want to be able to use windows and linux. To me reading fat 32 files is an essential part of the operating system. I do not want to add on something to do the job. 

My present version does not allow me to read USB Drives made in windows. I want to be able to have a version of ubuntu that does this automatically. I want to be able to have a version that I CAN RECOMMEND to other people. One that contains all the basic features

---

### Post by Pumalite on 2008-09-27
Is the format of the USB that matters; not the version of Ubuntu

---

### Post by Sef on 2008-09-27
I have never had a problem with my usb drives on Ubuntu.  They have always been detected.

---

### Post by unclesirbobby on 2008-09-27
Well mine says fat 32. It does not open in Ubuntu. It says it cannot mount it. I tried another USB stick and that did not work too. Maybe its a cut down version. I got it installed on the computer when I bought it. Maybe I should install the version that I have downloaded.

---

### Post by vanadium on 2008-09-27
First thing to check is whether the file system on the USB is in a good shape. Ubuntu will not mount corrupted file systems.

---

### Post by Pumalite on 2008-09-27
Get Gparted Live CD and reformat your hard drive. It wouldn't hurt to check it with rescuecd (TestDisk)
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by vanadium on 2008-09-28
The easier way to check the disk is using the standard command dosfsck. Suppose /dev/sdc1 is your USB partition. Yours probably is not mounted, but if it is mounted, you need to unmount first

```

sudo umount /dev/sdc1
sudo dosfsck /dev/sdc1

```

This only diagnoses and shows if there is an error. To actually repair, use the -a or -r option (see also "man dosfsck")

```

sudo dosfsck -a /dev/sdc1

```

---

