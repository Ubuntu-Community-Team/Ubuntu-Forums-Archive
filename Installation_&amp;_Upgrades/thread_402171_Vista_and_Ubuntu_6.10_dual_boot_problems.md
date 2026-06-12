---
title: "Vista and Ubuntu 6.10 dual boot problems"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by jamieb122 on 2007-04-05
Ive been searching the forums with no luck to my problem:

  I have two hdd's in my desktop.  I disconnected one hdd and installed Vista on it, then disconnected that and installed Ubuntu on the second hardrive.  Both drives are SATA.  I tried to modify my grub to be:
            root (hd1, 0)
            makeactive
           chainloader +1
 to try to load Vista, however this just restarts the computer.  I did however notice if I go into the bios and set to boot from the hardrive Vista is on, it boots fine.  Similarly if I set the biios to boot from my Ubuntu drive, it boots fine.  Im just not getting any love from grub and have tried to follow the steps many people have in the forums with no luck.  Any help is appreciated.




Thanks

---

### Post by confused57 on 2007-04-05
> **jamieb122 said:**
> Ive been searching the forums with no luck to my problem:

  I have two hdd's in my desktop.  I disconnected one hdd and installed Vista on it, then disconnected that and installed Ubuntu on the second hardrive.  Both drives are SATA.  I tried to modify my grub to be:
            root (hd1, 0)
            makeactive
           chainloader +1
 to try to load Vista, however this just restarts the computer.  I did however notice if I go into the bios and set to boot from the hardrive Vista is on, it boots fine.  Similarly if I set the biios to boot from my Ubuntu drive, it boots fine.  Im just not getting any love from grub and have tried to follow the steps many people have in the forums with no luck.  Any help is appreciated.




Thanks

You need a couple of map commands to boot Vista on a 2nd hard drive:
```
title              Windows Vista
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

See the 3rd link in my signature.

---

