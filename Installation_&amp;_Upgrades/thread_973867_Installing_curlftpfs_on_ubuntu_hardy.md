---
title: "Installing curlftpfs on ubuntu hardy"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by Dolxor on 2008-11-07
Im running Ubuntu in VMWare and wish to implement CurlFTPFS.

Problem is that i cannot get FUSE wokring.

uname -a
> 
Linux vps.cyberwarriors.nu 2.6.18-028stab057.2 #1 SMP Mon Jul 21 15:33:04 MSD 2008 i686 GNU/Linux


modprobe
> 
(nothing)


/etc/init.d/fuse start
> 
/usr/local/bin/fusermount
Loading fuse module failed!


ls -lah /dev/fuse*
> 
crw-rw-rw- 1 root fuse 10, 229 Nov  4 11:01 /dev/fuse


cat /etc/group | grep fuse
> 
fuse:!:115:dolxor


So. any ideas as what is wrong? I'v been scanning the internet looking for answer, yet to find any reasonable clues for solving my problem.

---

### Post by Dolxor on 2008-11-07
bump :)

---

### Post by Dolxor on 2008-11-10
Bump again.

Perhaps this is not the correct forum to post such as problem?:confused::confused::confused:

---

### Post by Dolxor on 2008-11-12
Bump..?

---

