---
title: "Running Ubuntu from a CD"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by Pondoro on 2010-08-17
If I boot Ubuntu from a CD can I access the files stored on the computer's (windows format) hard drive? If so where are they? I can find files in the shared area of my LAN but I cannot seem to find files on the hard drive of the PC that is running Ubuntu.

---

### Post by lechien73 on 2010-08-17
After starting up Ubuntu, go to the "Places" menu. You should see "xxGb Filesystem" listed, where "xx" is the size of your Windows partition. Click on this filesystem to mount it.

Otherwise, open a terminal window and type:
```
sudo su
fdisk -l
```
Make a note of which partition contains the NTFS file system
Type:
```
mkdir /media/windows
mount /dev/sdxx /media/windows/ -t ntfs

```
Change "sdxx" to the name and number of the NTFS partition you noted earlier.
Your Windows files should now be accessible through /media/windows

---

