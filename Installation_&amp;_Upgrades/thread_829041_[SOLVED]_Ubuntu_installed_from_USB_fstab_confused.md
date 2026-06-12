---
title: "[SOLVED] Ubuntu installed from USB: fstab confused"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by hoboken on 2008-06-14
Hey there guys. My CD burner is busted, so I tracked down a tut and installed the OS from a pendrive instead. Everything went surprisingly well (the liveos was blazingly fast, too) until I plug in my external hard drive...

"cannot mount, invalid mount option". 

OK, thanks. A bit of poking around the fstab and I realise that in addition, ubuntu has mistaken my pendrive for cdrom0. Reminds me of a chick hatching and thinking you're its mother - cute, but very annoying.

l@pan:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d40591e7-a056-45d0-a159-a5875c9682a9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=d3c501f6-89a1-42e9-bbfc-85757d4eae59 none            swap    sw              0       0
# /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0    0
# /dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0   0

Somebody advised to comment out the last two lines, and now when I log in it says "failed to initialise Hal", and the volume mounts, but is unreadable. I tried uninstalling and reinstalling Hal, only to break the GUI completely. Broke my repos, too, but that's a different story. Needless to say, a reinstall quickly followed. 

The solution must lie in either the fstab or the mtab, but I have no idea where to go from here. Ideas?

---

### Post by hoboken on 2008-06-15
bump. Nobody else installed ubuntu from USB?

---

### Post by PmDematagoda on 2008-06-15
Remove the entry for sdb1, then if there is a HAL problem try doing:-
```
sudo /etc/init.d/hal start
```

---

### Post by hoboken on 2008-06-15
Wow! PmDematagoda, that worked like a charm. Devices aren't mounting automatically, but I think I can take it from here.

So, what was happening? fstab thought sdb was a cdrom, removing its entry put everything back in its place? What was getting me was the fact that a couple of my errors said the the USB device had no entry in the fstab. Oh well..

Thanks a million!

---

### Post by PmDematagoda on 2008-06-15
Yes, it is very likely that the auto-mounter thought that the external drive was a CD-ROM and tried to mount it in ISO format which of course doesn't mount it at all. But about the new automatic mounting problem, perhaps you could include the proper fstab entry to be used with the external drive or create a script that will manually mount the drive for you.

---

