---
title: "Grub wants to update on a new dual boot setup, should I let it?"
date: 2009-11-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by k3lt01 on 2009-11-08
I have setup my laptop to run Karmic and also Lucid. it is setup like this;
10 gb / for Karmic
10 gb / for Lucid
2 gb SWAP
140 gb /home for Karmic
50 gb approx /home for Lucid.

Both will boot easily and no problems so far at all. I did an update to get Lucid going and it had a Grub update. I was asked if I wanted to stay with the Grub installed today of the LiveCD or if I wanted to go with the Maintainers new version. As soon as I said stay with the current version it had a minor crash, no big issue boots fine still into both / partitions.  So I wonder should I let it update GRUB or should I just stay with the Karmic version? This is my main machine but I do have a copy of all my stuff on my desktop and an external hdd.

---

### Post by philinux on 2009-11-08
I always choose the package maintainers version.

With one hard drive you only really need one grub installed to the mbr. However if you like to keep your grub menus tidy, I do, then this thread may help.

[http://ubuntuforums.org/showthread.php?t=1315669](http://ubuntuforums.org/showthread.php?t=1315669)

---

### Post by k3lt01 on 2009-11-08
Thanks Phil, will take a look at that link tonight.

---

### Post by philinux on 2009-11-08
> **k3lt01 said:**
> Thanks Phil, will take a look at that link tonight.

Just had the grub update on karmic. I said use the package maintainers version and that overwrites /etc/default/grub. I wont do this again with grub2. It's no big deal as the only mod I made to that file was

GRUB_DISABLE_OS_PROBER=true

---

### Post by k3lt01 on 2009-11-08
> **philinux said:**
> Just had the grub update on karmic. I said use the package maintainers version and that overwrites /etc/default/grub. I wont do this again with grub2. It's no big deal as the only mod I made to that file was

GRUB_DISABLE_OS_PROBER=trueSo there is no need to modify GRUB then, just let it install the new version and be done with it?

---

