---
title: "ubuntu couldn't detect the latest mother board"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by djalil on 2007-03-22
Hi
    I like Ubuntu linux, I propose it to my IT company, but we have a new computers, with advensed mother board, and it seam Edgy can't run on it, when you try to installed it is very slow, then when it finish he can't get the internet, so it's tow problem, why it's slow, is it because he can't recognize some hardware in my computer becaue it the latest technology, and also is not able to configure the network card.
 
    I tried to read the manual for the mother bord, there is part about linux, but not for ubuntu linux when you try to do it there many errors apear.

   So should i wait for the next release of ubuntu or is there a way (easy) to configure the hardware speacily the new ones, for example now intel release the quadripol prossesor


Djalil

---

### Post by wpshooter on 2007-03-22
Unless I had a great deal of expertise in Linux, I don't believe that I would be proposing that my company go to Ubuntu at this time, especially if my job depended upon it.

---

### Post by dannyboy79 on 2007-03-22
why don't you tell what northbridge and southbridge your motherboard has??? Also, when you boot to the live cd, open a terminal and type in 
sudo lspci -v
so we can see the chipsets.
I doubt that Ubuntu doesn't support it, it's probably that Ubuntu doesn't support it out-of-the-box.

---

