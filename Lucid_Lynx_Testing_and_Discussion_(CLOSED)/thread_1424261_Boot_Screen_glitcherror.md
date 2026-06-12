---
title: "Boot Screen glitch/error?"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Cam! on 2010-03-07
Whenever I boot LL Alpha 3 up, I get a black screen, and what looks like a giant terminal. I press "enter", I get some text, and a small "Ubuntu" logo on a purple background.

What should I do to fix this?

---

### Post by VMC on 2010-03-07
> **Cam! said:**
> Whenever I boot LL Alpha 3 up, I get a black screen, and what looks like a giant terminal. I press "enter", I get some text, and a small "Ubuntu" logo on a purple background.

What should I do to fix this?

A couple of things. First, what hardware do you have.
From grub menu, edit and remove the "quiet" from the "linux" line.
 Then what's the last text message you see.
Also , if that doesn't reveal anything, from grub menu, add "nomodeset" to the end of "linux" line.

---

### Post by Cam! on 2010-03-07
I have an Intel Q660 2.4GHz x64 CPU, 4GB's of RAM, an ATI Radeon HD 4850 graphics card, and x64 Ubuntu.

---

### Post by ViperScull on 2010-03-08
It happens the same to me sometimes.

I have autologin enable. Sometimes i boot normal and autologin, sometimes (less than the other case) i get a black screen until i press enter, then go to gdm for a normal login (not autologin).

---

