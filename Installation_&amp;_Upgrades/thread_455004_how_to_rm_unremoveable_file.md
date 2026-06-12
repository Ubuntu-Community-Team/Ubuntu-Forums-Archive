---
title: "how to rm unremoveable file"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2007-05-26
I think I've got a corrupted /var/cache/apt/pkgcache.bin   file   but I can figure out how to 
remove it.  Is there some majic trick that will help me overcome this?  The file has a sticky bit and a ? for the file type!  I've managed to "touch" the file and hence update the date but can not remove it, edit it or anything.

Is there a way to become this user number ... ?  7157577   ?

I've tried fsck and it says no problem ...

Thanks for any suggestions, have seached and googled and no lukc

Thanks a  bunch

Jim

----------------------------
ubuntu@ubuntu:/media/disk/var/cache/apt$ ls -al
total 16540
drwxr-xr-x  4 root    root       4096 2007-05-25 15:32 .
drwxr-xr-x 20 root    root       4096 2007-05-14 11:19 ..
drwxr-xr-x  3 root    root      69632 2007-05-25 13:33 archives
drwxr-xr-x  3 root    root      73728 2006-04-15 07:36 archives.save
?rwxr--r-t  2 7157577 14009 876819778 2007-05-26 07:46 pkgcache.bin
ubuntu@ubuntu:/media/disk/var/cache/apt$ sudo rm pkgcache.bin 
rm: cannot remove `pkgcache.bin': Operation not permitted
ubuntu@ubuntu:/media/disk/var/cache/apt$

---

### Post by rillip on 2007-05-26
I would try 

sudo rm file

I believe you can also remove the sticky with 

sudo chmod -t xxx (whatever the permission should be... let's just say 644 for the sake of argument)

Maybe try (or maybe run man on chmod first to ensure that flag is right) that and then try to remove it as root again.

---

### Post by bigken on 2007-05-26
this might sound daft but I had the same problem with some files on my desktop no what I did I could not remove or delete them so what I did was create a new folder dropped the offendings files into the folder and deleted it

---

### Post by jamaas on 2007-05-26
Thanks guys,

I figured out a rather crude solution.  I just created a new directory called apt2, copied over the good files/directories, renamed the apt  directory aptold and then renamed the new directory apt ...

So the old file is still hanging around but not causing problems ... now if I can just figure out how to erase it .... 

Thanks

Jim

---

