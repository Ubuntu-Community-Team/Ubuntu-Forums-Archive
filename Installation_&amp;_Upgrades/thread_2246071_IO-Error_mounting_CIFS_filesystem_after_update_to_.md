---
title: "IO-Error mounting CIFS filesystem after update to kernel 3.13.0-36-generic"
date: 2014-09-28
forum: Installation &amp; Upgrades
---

### Post by mkrueger2002 on 2014-09-28
Hello,

after routinely update to the current linux-image-lts-trusty, which is version 3.13.0-36, I cannot longer mount files via CIFS-filesystem.
In my fstab I defined

//192.168.3.110/martin /media/NAS/martin cifs noauto,user,credentials=/home/martin/.smbcredentials,uid=1000,gid=1000,nodfs 0 0

so that with the command

mount /media/NAS/martin

I was able to mount my files on the NAS. This is not longer possible since the update to the former mentioned kernel-version: I get an IO-Error of the CIFS filesystem.
I returned to the kernel 3.13.0-35-generic, and all works fine.

Does anybody have the same problem ??
Is it a known problem of kernel version 3.13.0-36 ??

Thanks for your help,

Martin

---

### Post by TheFu on 2014-09-28
nodfs is not shown as a valid option in my systems. Are you certain that works on yours?

---

### Post by mkrueger2002 on 2014-09-28
@ TheFu

... everything has been working fine for nearly two years (I run 12.04 on my computer). Maybe nodfs is an old option ?? I also can't find it in the current documentation - but fact is, that there is no mount error with kernel 3.13.0-35.

---

### Post by Morbius1 on 2014-09-28
Possible bug?  [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372482"]mount.cifs does not work with the 3.13.0.36-generic kernel 
[/URL]

---

### Post by TheFu on 2014-09-28
3.13.0-36-generic - works here.
I'm using autofs, however.

/etc/auto.Data:
```
K        -fstype=cifs,rw,iocharset=utf8,file_mode=0666,dir_mode=0777,credentials=/etc/samba/win7lap-D.credentials  ://172.22.22.14/K
```

---

