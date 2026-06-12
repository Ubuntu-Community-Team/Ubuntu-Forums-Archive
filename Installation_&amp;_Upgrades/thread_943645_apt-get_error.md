---
title: "apt-get error"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by zoobave on 2008-10-10
When i try to install/upgrade any package, i am getting the following error.

```
dpkg: syntax error in triggers Deferred file `/var/lib/dpkg/triggers/Unincorp' at character `U' midline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by jamesrl on 2008-10-10
Can you see what's in the directory and then the file?

From the terminal type 
```

ls -la /var/lib/dpkg/triggers/
sudo cat /var/lib/dpkg/triggers/Unincorp

```

Actually looking up the file gave this thread that has the solution to the same problem:

[http://ubuntuforums.org/showthread.php?t=681675]("http://ubuntuforums.org/showthread.php?t=681675")

By the way the output on my system is 
```
$ ls -la /var/lib/dpkg/triggers/
total 20
drwxr-xr-x 2 root root 4096 2008-09-28 02:16 .
drwxr-xr-x 7 root root 4096 2008-10-08 20:41 ..
-rw-r--r-- 1 root root    6 2008-09-28 02:16 ldconfig
-rw------- 1 root root    0 2008-10-08 20:41 Lock
-rw-r--r-- 1 root root    0 2008-09-28 02:16 Unincorp
-rw-r--r-- 1 root root    5 2008-04-22 18:18 update-grub
-rw-r--r-- 1 root root   16 2008-08-20 05:14 update-initramfs

$ sudo cat /var/lib/dpkg/triggers/Unincorp 
$

```
e.g., Unincorp is an empty file.

---

### Post by zoobave on 2008-10-11
thanks,  the problem has been solved now.

---

