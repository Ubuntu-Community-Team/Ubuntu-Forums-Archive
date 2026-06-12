---
title: "[SOLVED] grub error 15 can't boot XP or Ubuntu"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by karrank% on 2008-07-30
tried to install Dapper over Hardy on my dualboot and now  boot stops after displaying grub error 15. Anyone has (or preferably had, since solved) a similar problem?
-thanks

---

### Post by xen-uno on 2008-07-30
... which is File not Found. See ...

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

A SuperGrub disk may fix your problem as well ... [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) or [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by karrank% on 2008-07-30
thanks, I'll look as soon as I can

---

### Post by john_smith_95030 on 2008-07-31
> **karrank% said:**
> tried to install Dapper over Hardy on my dualboot and now  boot stops after displaying grub error 15. Anyone has (or preferably had, since solved) a similar problem?
-thanks
i have had that problem many times, and the solution was the super grub disk. boot from it and selct bot mbr windows :(((((((((((
and it will boot you back into windows to manage your partitions. i forgot the place to get the supergrub isk, but search it. you may have to search and burn it on a different comp tho....but also sadly u will have to reinstall ubuntu.

---

### Post by markbuntu on 2008-07-31
Rather than having to reinstall Ubuntu or using supergrub, you should try the chainload option in grub first. It fixed my problems with dual booting into two different Ubuntu installs, each with its own grub which mysteriously stopped working suddenly and will also work for windows and every other os you can think of. It just passes the entire boot operation to the partition you select. And no Error 15 messages.

If you know which partitions your boot sectors are on, edit your grub/menu.lst and add these lines.
```

#chainload Ubuntu

root        (hd0,0)
chainloader  +1

#chainload XP

root       (hd0,5)  
chainloader   +1

```
You can change the (hdx,x) to your actual boot partitions. Be patient, it may take a few seconds after the selection before the boot starts. There is more info on grub boot options here:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

EDIT: I'm sorry, I wrote chainload instead of chainloader in the above, it has been fixed

---

