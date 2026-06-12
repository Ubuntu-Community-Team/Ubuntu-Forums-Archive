---
title: "auto mount of USB flash"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by mvdberg112 on 2008-06-16
When a USB-flash-drive is inserted, the drive is automatically mounted, and the directory is automatically given the permissions of the user logged in to GNOME. Which piece of software make this happen? And how does it know which name to use? Because Linux is a multi-user OS after all. This are the permissions for the directory where the USB stick is mounted to:```
root@server01:/# ls -l /media
total 50
....
drwx------ 2 user    root       16384 1969-12-31 19:00 disk
....

```

Why does this line in the fstab not work? Why does the automatic mounter in Linux not have enough permissions? ("cannot mount volume you are not privelidged to mount this volume")

Using Gutsy.

Thanks for any help. I see on forums a lot a people who had this error message and tried to search in the Launchpad database, but never a in depth explanation.

---

