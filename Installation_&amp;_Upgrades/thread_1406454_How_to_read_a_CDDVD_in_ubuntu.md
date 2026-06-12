---
title: "How to read a CD/DVD in ubuntu?"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by karumudi7 on 2010-02-14
Hi today I got a big question, when I put CD into my drive it was not showing the contents of the drive.
I think we have to mount, but how?  I run the following commands:

> nani@ubuntu:~$ sudo mkdir /media/CD
mkdir: cannot create directory `/media/CD': File exists
nani@ubuntu:~$ sudo mount /dev/cdrom /media/CD
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/CD busy
mount: according to mtab, /dev/sr0 is already mounted on /media/CD
nani@ubuntu:~$


---

### Post by Mark Phelps on 2010-02-14
You shouldn't have to manually mount the CD drive.  When you insert a CD, you should get an icon on the desktop.

If you're not getting that icon, go to Places and see if there is a device icon in there and click that.

---

### Post by karumudi7 on 2010-02-14
I am using KUbuntu..!

---

