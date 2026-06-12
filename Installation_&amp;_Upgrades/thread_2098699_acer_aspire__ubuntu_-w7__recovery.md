---
title: "acer aspire / ubuntu -w7 / recovery"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by trasgo77777 on 2012-12-27
Hello! I installed ubuntu in my acer aspire one but i need w7 as well. I dont have cd.
My partitions are:

recovery / swap / ubuntu / blank space for w7

1. Is it possible to install w7 from recovery in the blank space? What kind of partition should do?

2. If it is no possible, what i need to do to recover all the w7? Only one partition? What kind of partition? Maybe the easiest way is to decrement w7 partition from w7 and then install linux.

I can open recovery from grub

---

### Post by wyliecoyoteuk on 2012-12-27
Option 2 is probably the best way to go, installing windows will wipe any Linux boot.
Recover windows, reduce the partition and then use a USB stick to  install Ubuntu in the empty space.

---

### Post by trasgo77777 on 2012-12-27
Ok, i am going to create a big primary partition with swap linux and blank space. I pray for that recovery works

---

### Post by trasgo77777 on 2012-12-28
Ok, i win :popcorn:
 
Some things:
 
To recover, the w7 needs a primary partition bigger than 22 gigas. I cant format as nffs so i format with fat 32 ( 32 gigas is the bigger that can be) I would be great if ubuntu allow format ntffs with the live versions. Another thing, w7 didnt delete the grub so i dont need to install it again. ):P

---

