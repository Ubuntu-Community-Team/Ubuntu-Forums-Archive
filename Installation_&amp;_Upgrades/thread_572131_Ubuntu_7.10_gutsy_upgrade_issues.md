---
title: "Ubuntu 7.10 gutsy upgrade issues"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by addiekaul on 2007-10-10
Hello Experts,

I recently upgraded from 7.04 to 7.10 and seem to have some issues.

If i boot with 2.6.22-* kernel am not able to login with my username as it throws /home/user directory not found.

Booting with  2.6.20-16-386 kernel am able to  login to my /home dir.

Kindly let me know if am doing something wrong here.

I have a separate /home partition.

Thanks,
Addie

df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             17132816   8341060   7921440  52% /
varrun                 1037612       160   1037452   1% /var/run
varlock                1037612         4   1037608   1% /var/lock
udev                   1037612       124   1037488   1% /dev
devshm                 1037612         0   1037612   0% /dev/shm
lrm                    1037612     34504   1003108   4% /lib/modules/2.6.20-16-386/volatile
/dev/sdb5             60476036  49604364   7799644  87% /home

---

### Post by gwoodard on 2007-10-10
Cant people just wait for the official version and not update with the BETA version...7.10 still has bugs

---

### Post by misfitpierce on 2007-10-10
Well it's in beta so people can help find bugs. I would say wait if you just want it. If you however want to help with 7.10 then you upgrade.

---

### Post by addiekaul on 2007-10-13
Any idea how to fix this issue ?

---

### Post by kamillozo on 2007-10-13
> **addiekaul said:**
> If i boot with 2.6.22-* kernel am not able to login with my username as it throws /home/user directory not found.
Booting with  2.6.20-16-386 kernel am able to  login to my /home dir.

I got exactly the same problem as you described. But i don't treat this problem as important because i got another kernel working. Unfortunately I got also problem with fglrx driver on working kernel - I have no 3d accelleration and thus no compiz fusion working.  Maybe I will describe it in new thread.

---

