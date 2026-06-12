---
title: "Increasing Partition Size"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by Kavkaz86 on 2008-08-08
Hello Ubuntu Members,

I'm currently running Ubuntu on dual boot. When I first installed it, I used the smallest partition because I was new with Ubuntu. Now I want to increase the partition without formatting the drive and I want to keep it on Dual boot. How could I do that?

---

### Post by geoffjay on 2008-08-08
you could try doing a dd of your root partition to back it up then boot a live cd and run fdisk on your drive. delete the partition, and reallocate more space. after that restore to the new partition.

see:
[http://www.cpqlinux.com/ddbackup.html](http://www.cpqlinux.com/ddbackup.html)

but you might be better off just backing up your /home and config files and starting over.

---

