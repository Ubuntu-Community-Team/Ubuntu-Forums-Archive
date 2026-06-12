---
title: "50% Ubuntu 50% Windows, how to make it 100% Ubuntu ?"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by michael-piziak on 2014-03-07
My sister has decided to install Ubuntu on 50% of her system because her Windows desktop has come to a crawl.  I can tell her how to do that.  However, in the future, if she wants to go 100% Ubuntu and wipe the 50% Windows partition out, how would she go about doing it ?

---

### Post by grahammechanical on 2014-03-07
There are two ways.

1) After backing up all that data she wants to keep, install Ubuntu again using the Use the Entire Disk option.

2) After backing all the data that she does not want to lose, run the Ubuntu live session and Use Gparted to delete the Windows partitions and to expand the Ubuntu partition to take up the unallocated space. Then run Ubuntu and in a terminal run

```
sudo update-grub
```

And that should modify the Grub boot menu to remove the link the Windows.

Cannot be more specific without having more specific knowledge of the partitioning scheme that you end up with.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Ask here for help at the time that you want to do this.

Regards.

---

### Post by Ubi_one_2014 on 2014-03-08
from my point of view.

let her backup all nessacerry docs, etc, and install ubuntu and let ubuntu choose all hd's, so windows got wiped out forever

---

