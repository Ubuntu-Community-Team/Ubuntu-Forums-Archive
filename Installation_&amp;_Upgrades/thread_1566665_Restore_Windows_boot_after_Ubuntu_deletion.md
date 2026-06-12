---
title: "Restore Windows boot after Ubuntu deletion"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by jibarz on 2010-09-02
Hi all,

I've deleted all linux partitions meaning swap, / and /home and now only get an "error: no such partition". I've noticed I've deleted also /boot partition, so, is there a solution to fix windows 7 boot without any windows cd? Linux commands, live cd, etc.??

Many thanks.

---

### Post by bcbc on 2010-09-02
You should have replaced the grub bootloader in the disk MBR before deleting linux. 

Boot the live CD, run 
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Ignore the warnings you get when you install lilo

---

