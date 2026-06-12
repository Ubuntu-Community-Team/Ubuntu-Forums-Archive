---
title: "Unable to mount location!"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by jazerix on 2010-06-25
So I just installed Ububtu on my laptop and now im getting this error "Unable to mount location - Not Authorized" when I'm trying to open the partition, the problem is that i got all my backup on it, and I'm afraid I have to go back to Windows if I can get this working >:).

Any help is appreciated

---

### Post by dino99 on 2010-06-25
if you want help, you first need to give us real info: which ubuntu release is installed, how is formated this device you cant mount.

the minimum packages required: ntfsprogs & ntfs-3g
check into synaptic about them, and install them if not

then install mountmanager to set your prefs about partitions and devices rights (system admin mountmanager)

---

### Post by jazerix on 2010-06-25
Lets see, im running Ubuntu v. 10.04
Tbh, I did the thig where u can still launch windows (its on my other harddisk)

got 2x 500GB Harddisks in this laptop
i believe all my partitions are NFS but im not sure...

---

### Post by catsails on 2010-06-26
I am now getting this same error, though it's new. I was able to access the partition as of 2 days ago, but now I can not.  I am running ubuntu 10.04, installed with wubi. I am thinking this could be caused by downloading and installing something, but I have the update manager set to automatically download stuff every 2 days, and looking at the log in /var/log, it looks like many things were done on the 24th, from open office stuff to cups, python things, libmysql, etc. 

Using the disk utility I found the name of the drive, then tried sudo mount /dev/sda, but got the error that it couldn't find it.

---

