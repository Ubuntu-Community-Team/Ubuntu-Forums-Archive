---
title: "Complete harddrive backup"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by Sudo Bash on 2014-02-03
Hello all,

What is the best way to perform a complete harddrive backup? I am going to wipe my harddrive and install a different variant from the ubuntu 12.04 vanilla. I have heard of clonezilla, FSArchive before, but do I even need any software like that? I want to make two backups. One backup would dump the entire contents of the harddrive (including partition table) to make a copy that I could restore from if I needed to revert the computer back to the installation I had. The other backup would be a copy of the files (in particular the usr and etc directories) in an easy to access form so that I could copy my files and document back to my fresh install.

For the first task, could I just use dd on the /dev device to back up to an external harddrive an image file. Then for the second task, could I just use cp -r to copy all the directories other than /tmp /proc /dev and /sys?

---

### Post by TheFu on 2014-02-03
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

There are many, many different tools depending on the real requirement. Some are extremely thorough, but slow. Others are efficient on space, but don't store the backup files in an easily usable manner.  Others are image-based, so lots of storage gets wasted.  If you know the system and the data on it well, it is possible to get everything that makes some systems unique backed up in under 50MB of storage. 

So - it all depends on your needs.  My signature has other backup links too.

Linux is a multi-user system, so file permissions, user and group settings are a critical part of the backups.  There are other sorts of files that cp won't handle properly, so that is probably NOT a good backup method.

---

