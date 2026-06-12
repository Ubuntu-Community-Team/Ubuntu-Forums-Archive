---
title: "cifs/samba failed after upgrade 20.04 to 22.04"
date: 2022-08-22
forum: Installation &amp; Upgrades
---

### Post by mark@qtrac.eu on 2022-08-22
I have been using cifs to access a USB memory stick attached to my router for the past few years, first with Ubuntu 18.04, then with 20.04.

Since updating to 22.04 this has stopped working and I don't know how to solve the problem.

Here's some information which I hope will help someone to help me:

```

$ grep cifs /etc/fstab 
//192.168.1.1/volume(sda1)/    /media/n    cifs    user=mark,password=,uid=1000,gid=100,rw,user,auto,vers=1.0    0    0

$ dir /media/n
total 0
$ dir /media/
total 8.0K
drwxr-x---+ 3 root root  4.0K Aug  5 18:57 mark
drwxrwxrwx  2 mark users 4.0K Oct 21  2015 n

$ sudo dmesg|grep cifs
[sudo] password for mark: 
[   10.614599] FS-Cache: Netfs 'cifs' registered for caching
[   10.617397] Key type cifs.spnego registered
[   10.617414] Key type cifs.idmap registered
[   10.617820] CIFS: VFS: cifs_mount failed w/return code = -101
$ sudo mount /media/n
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)

```

I then installed smbclient and tried it:
```

smbclient -L //192.168.1.1/volume\(sda1\)/
protocol negotiation failed: NT_STATUS_CONNECTION_DISCONNECTED

```

So now I'm wondering if the problem is with samba rather than cifs?

I still have a computer using Ubuntu 20.04 which has exactly the same folder and fstab line and works fine.

---

