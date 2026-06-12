---
title: "install crash"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by hirohitosan on 2008-03-26
hi there. I install the ubuntu on my computer when suddenly a power failure occur and my computer was turned off. I tried to start again the installation and when I arrive at the disk partitioning an error occur:
```
File system was not cleanly unmounted! You should run e2fsck. Modifying an unclean file system could cause severe corruption.  
```

How can I use e2fsck?
what parameters?

I tried to read the man page but there are so many options and I'm afraid to not make a mistake.

Can anyone help me?

Thanks

---

### Post by PmDematagoda on 2008-03-26
In the Live CD please post the outputs of:-
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

---

