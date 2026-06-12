---
title: "How to Verify OS version"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by donwoodsnet on 2007-12-29
I have UBUNTU 6.10 running on a Core 2 Duo. I don't remeber whether the OS is 64bit. How do I verify?
When I log into the console it says:
2.6.17.10-server #2 SMP Tue Dec 5 22:29:32 UTC 2006 I686.

---

### Post by seshomaru samma on 2007-12-29
run this command:
```
uname -asoi
```
i'm on 32bit so my output is:
```
Linux desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
```
if it's 64bit you should get something like:
```
Linux desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 **x86_64 **GNU/Linux
```

---

### Post by donwoodsnet on 2007-12-29
Thanks. I guess that explains why my system clocks like mad when I try to upgrade to 8 gig of ram. ](*,)

---

### Post by Sef on 2007-12-30
> Thanks. I guess that explains why my system clocks like mad when I try to upgrade to 8 gig of ram. 

The 32-bit version can't use more than 4 gb of ram.

---

### Post by donwoodsnet on 2007-12-30
> **Sef said:**
> The 32-bit version can't use more than 4 gb of ram.
Isn't there a kernel option to allow more then 4gig?

---

