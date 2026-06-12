---
title: "Dual Boot single 40GB Drive"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by geek2330 on 2007-08-25
My friend just asked me this question and there are hundreds of posts with mixed feedback....so I decided to ask the question quickly here.

He has 1 IDE 40GB drive and will have 2 partitions. He wants to have both XP and Ubuntu.

1. Wondering if Ubuntu should go first on the C drive.
2. Or should load XP first on C, then boot with Ubuntu Live CD and install Ubuntu on D partition.

If option 2 is the way to go, then what about Grub?

.

---

### Post by Pumalite on 2007-08-25
Is best to have XP in sda1 (C) installed first and then install Ubuntu in sdb(D) and have Grub installed to MBR(hd0). You will have Grub with a menu to boot either one.

---

### Post by geek2330 on 2007-08-25
ahhh, thanks.

---

### Post by Pumalite on 2007-08-25
You are welcome. Anytime!

---

### Post by pgar23 on 2007-08-25
If this thread is solved...would you mind marking it as SOLVED by going to thread tools @ the top of the page and select mark this thread SOLVED.

---

### Post by Pumalite on 2007-08-25
Looks like solved to me!

---

### Post by pgar23 on 2007-08-25
> **Pumalite said:**
> Looks like solved to me!
I realized that it was solved, thats y I'm suggesting the owner of the post to mark as SOLVED.

---

