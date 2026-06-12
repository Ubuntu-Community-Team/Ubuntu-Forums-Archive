---
title: "Problem booting linux virtual kernel"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by andrew1992 on 2011-02-20
Hello all, 

I installed Ubuntu 10.10 on VirtualBox with a windows 7 host, which is  working fine. However, it has been pointed out to me that I can get  better performance with the linux virtual kernel. I downloaded the  package, but upon trying to boot with this kernel, I get the following  error message:



ALERT! /dev/disk/by-uuid/de2ab591-35b0-4cf0-a328-1e458ebbfd30 does not exist. Dropping to a shell!



I have no idea how to solve this problem. Upon looking in /dev, it  appears as though there is no /disk directory.  Anybody know how to  solve this problem?

---

### Post by andrew1992 on 2011-02-20
After some googling, I've discovered that this is perhaps an issue with the initrd file. I can still boot the generic kernel (before the installation of the virtual kernel), and in my root directory are the following:
```

andrew@ubuntu:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
andrew@ubuntu:/$ 

```

I noticed there is an initrd.img as well as an initrd.img.old.  Looking in /boot:

```

andrew@ubuntu:/boot$ ls -l initrd*
-rw-r--r-- 1 root root 10754794 2011-02-19 14:53 initrd.img-2.6.35-22-generic
-rw-r--r-- 1 root root 10755599 2011-02-20 09:38 initrd.img-2.6.35-25-generic
-rw-r--r-- 1 root root  4153071 2011-02-19 17:05 initrd.img-2.6.35-25-virtual
andrew@ubuntu:/boot$ 

```

The VIRTUAL initrd.img seems to be much smaller than the generic, which leads me to believe that this file is the cause for the error message upon booting:
```

missing modules (cat /proc/modules; ls /dev)

```

So, does anybody have any suggestions for fixing this file, so I can boot the virtual kernel?

---

### Post by andrew1992 on 2011-02-20
bump.

---

### Post by andrew1992 on 2011-02-22
Anyone have any ideas?

---

