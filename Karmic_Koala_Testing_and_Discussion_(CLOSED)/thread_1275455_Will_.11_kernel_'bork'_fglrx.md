---
title: "Will .11 kernel 'bork' fglrx?"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-09-25
Well after all this time, they finally got 'fglrx' working. I see there is a kernel upgrade tonite ( from .10 to .11) and was wondering if it's gonna play nicely with 'fglrx'.

---

### Post by VMC on 2009-09-25
Try it. If you applied the current updates you have it in your /boot. Just edit grub2 and change from 10 to 11 and boot.

It's not going to hurt to test it.

---

### Post by DougieFresh4U on 2009-09-25
> **VMC said:**
> Try it. 

It's not going to hurt to test it.

That's what were here for. And it's no big deal to fix **IF** it doesn't work.

---

### Post by DougieFresh4U on 2009-09-25
All went well with installing the .11 kernel. Nothing 'borked', 'fglrx' is working as should be. Had to go and update my 32 bit install as well and update-grub2 there to get everything in working order on this multi boot system.

---

### Post by Regenweald on 2009-09-25
Didn't break Nouveau :)

---

