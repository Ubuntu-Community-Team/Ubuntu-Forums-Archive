---
title: "Just installed Lucid alpha3 from thumb drive, but x fails to start."
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vs8 on 2010-02-26
All I see is the white Ubuntu logo and the cursor hanging in the middle of the screen. ctrl+alt+F1 is all I can do, I updated the system hoping it was a driver bug but the problem persists.

Please help me!!!!

---

### Post by VMC on 2010-02-26
> **vs8 said:**
> All I see is the white Ubuntu logo and the cursor hanging in the middle of the screen. ctrl+alt+F1 is all I can do, I updated the system hoping it was a driver bug but the problem persists.

Please help me!!!!

when grub menu appears, select the one you want, type 'e' then go to linux line, and at the end of line type ***nomodeset*** , then Ctrl+x to boot. See if that works. Also it you remove the ***quiet*** then you will be able to see some text before plymouth starts.

---

