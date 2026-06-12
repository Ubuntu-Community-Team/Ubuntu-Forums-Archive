---
title: "how do u install ubuntu on a different drive"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by biggeslooser on 2007-12-18
ok i have two hard drives.. on hardrive 1 i have windows vista and on hardrive 2 i have nothying. 


problems:
want to put ubuntu on second hard drive and i dont know which is which on the installation and i dont want to screw up with windows

can i use system restore if i accidentally installed on the main hard drive??

---

### Post by taurus on 2007-12-18
From the LiveCD, before you click on the Install icon, post the output of this command here to see which one is your Vista drive.  Bet it's the first one.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by biggeslooser on 2007-12-18
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       24975   190378282+   6  FAT16
/dev/sda3           24976       37609   101481209    7  HPFS/NTFS

thats wat i get now can u hel?

---

