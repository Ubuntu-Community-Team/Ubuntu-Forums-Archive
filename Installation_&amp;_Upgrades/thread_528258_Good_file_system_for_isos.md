---
title: "Good file system for isos?"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by maybeway36 on 2007-08-17
I have a seperate /home partition on my hard disk, so I can reinstall the OS on a different computer and keep my settings and files as long as I move the hard drive. It has plenty of ISOs on it (for Ubuntu, Knoppix, FreeDOS, etc.) Right now it is formatted with ReiserFS. Is there a file system that would be better at storing these kind of files?

---

### Post by Steveway on 2007-08-17
XFS is good for handling large files.

---

### Post by maybeway36 on 2007-08-17
I decided not to change it, because with ReiserFS you can shrink the filesystem.

EDIT: In case anyone's interested, I once backed up my entire home directory to a tar file and recorded the md5sum:
```
cd ~
tar -cvf all.tar *
md5sum all.tar > all.md5
```
I then copied it to another computer with Samba.

---

