---
title: "Live CD FULL, Delete files, but no more available disk space"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by emeraldinspirations on 2011-01-10
I am booting to the Live CD using a USB Flash drive.  When I first logged on there was some small amount of disk space.  Over time this disk space has reduced until there is now none left.  Now I can not even mount the main hard drive or any flash drives.

I am attempting to remove files from my main hard-drive to a backup drive before installing Ubuntu.  So in order to continue, I have to be able to mount the drives.

I have deleted every file I can from the Home folder (on the Live CD), emptied all the Trash folders (root included), deleted all the sample data, Firefox cache, Nautilus cache, and nothing adds any space.

I was planning on moving the home folder to my main hard drive to prevent this from happening again, but I can not because I can not mount the main drive.

I don't know what else I can do except re-burn the ISO.  I have attempted to download a replacement ISO (on a second computer) several times and each time the download stops somewhere 38 MB, 692 MB, 325 MB, but never fully downloaded.  There is never an error, it just says it is complete.  I have tried IE, FireFox, Google Chrome, etc. none of which can download the file.

I don't care about any of the settings or backups the Live CD is storing, I just want to be able to go back to removing my files from the main hard drive.

I don't know what else I can do.

```
ubuntu@ubuntu:~$ df -h
Filesystem        	Size  Used Avail Use% Mounted on
aufs              	124M  121M 	0 100% /
none              	491M  272K  491M   1% /dev
/dev/sdb1         	3.8G  822M  3.0G  22% /cdrom
/dev/loop0        	661M  661M 	0 100% /rofs
none              	497M  112K  497M   1% /dev/shm
tmpfs             	497M  2.0M  495M   1% /tmp
none              	497M   84K  497M   1% /var/run
none              	497M  4.0K  497M   1% /var/lock
```

---

