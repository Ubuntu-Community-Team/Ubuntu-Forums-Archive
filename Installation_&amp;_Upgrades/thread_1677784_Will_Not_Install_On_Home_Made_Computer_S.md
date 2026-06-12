---
title: "Will Not Install On Home Made Computer :S"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by ryanteck on 2011-01-29
Hi
For some reason ubuntu will not install onto my home built computer.

I have tried the normal 10.04 desktop install. and the minimum install.

I have swapped ide cables on both the hdd and the DVD rom drive and i am going to try out a different hdd.
Any help?

---

### Post by Frogs Hair on 2011-01-29
Have you done a checksum  or tested the cd with another computer to make sure it works? It beats changing hardware. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by sikander3786 on 2011-01-29
Can you please list any errors or problems you've encountered? Does the CD boot at all? What do you see?

---

### Post by ryanteck on 2011-01-29
the cd works on other computers.
i think it may be the graphics card as it keeps refreshing the screen when it crashes it still sounds like it is installing but i cant ever see nothing

---

### Post by cavh on 2011-01-29
Try reseating the graphics card in its slot (presuming it's not built into the motherboard) and also reseat the memory (cards can move slightly due to thermal expansion and subsequent cooling, aka 'socket creep').

---

### Post by ryanteck on 2011-01-29
New graphics card in and it works perfect. the graphics card was an ATI Radeon rex but a little downgrade to an older one worked perfect :)

---

### Post by sikander3786 on 2011-01-29
> **ryanteck said:**
> New graphics card in and it works perfect. the graphics card was an ATI Radeon rex but a little downgrade to an older one worked perfect :)
Glad you got it working.

With the problematic cards, you can use *nomodeset* to get past those errors. See here for details.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

