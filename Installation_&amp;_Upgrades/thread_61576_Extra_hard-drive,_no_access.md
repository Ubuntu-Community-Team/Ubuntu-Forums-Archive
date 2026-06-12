---
title: "Extra hard-drive, no access"
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by ruvil on 2005-09-01
Hello!
Today i have installed ubuntu on my computer with 2 hdds. I only can get access to the "/" mounted harddrive.
I cant access my other harddrive.. or.. i can access it.. but not create files in it. "root" is the owner.. root can write files to it and so on. But i can. How can i change the settings so i can write files to it and.. yeah.. so on? :mad:

---

### Post by Lord Illidan on 2005-09-01
What is the other mounted hard drive? NTFS, or FAT?

The details are important, please include them..

---

### Post by ruvil on 2005-09-01
[QUOTE=Lord Illidan]What is the other mounted hard drive? NTFS, or FAT?

The details are important, please include them..[/QUOTE]
 The harddrive i cant access is a ext2 harddrive. i can see it in ubuntu. but not access is.

---

### Post by Lord Illidan on 2005-09-01
You have to modify your /etc/fstab file..
I am currently at work using Windows at the moment or I would have done something...
Try looking at the ubuntu guide, under mounting fat32 drives read&write, and replace the fat32 with ext2.

---

### Post by ruvil on 2005-09-01
[QUOTE=ruvil]The harddrive i cant access is a ext2 harddrive. i can see it in ubuntu. but not access is.[/QUOTE]
 Maybe anyone here knows more exact how to do?

---

### Post by Lambert on 2005-09-01
You need to check your fstab folder in /etc. Sound like you need to adjust permissions for that drive. Here's a link with more information.

[http://www.debian.org/doc/manuals/debian-tutorial/ch-disks.html](http://www.debian.org/doc/manuals/debian-tutorial/ch-disks.html)

---

