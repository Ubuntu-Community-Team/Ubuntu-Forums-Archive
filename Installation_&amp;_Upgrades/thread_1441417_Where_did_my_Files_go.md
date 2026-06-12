---
title: "Where did my Files go?"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by TheWielder on 2010-03-28
I just switched my old computer from Windows ME to the lastest Ubuntu. It's working fine, except...

I can't find any of my files. 

In the Installation, it said it was deleting everything from my old OS, and Partitioning my Hardrive... Are they all gone?

---

### Post by derekeverett on 2010-03-28
> **TheWielder said:**
> I just switched my old computer from Windows ME to the lastest Ubuntu. It's working fine, except...

I can't find any of my files. 

In the Installation, it said it was deleting everything from my old OS, and Partitioning my Hardrive... Are they all gone?

oh no! I'm sorry but it sounds like you wiped everything out!

Did you have any of your files backed up?

When you were installing Ubuntu did you select to use the entire drive?

---

### Post by sailthesea on 2010-03-28
Doesn't sound too good...
If you had your files in a separate partition they may have survived. Did the Windows setup have the OS on Drive C: and data on D: ? 
 A data recovery program might get some of them back
 I'm not sure which is the best one to use with the current Ubuntu

 Stick with it someone will help you out

 Welcome by the way:)

---

### Post by presence1960 on 2010-03-28
> **TheWielder said:**
> I just switched my old computer from Windows ME to the lastest Ubuntu. It's working fine, except...

I can't find any of my files. 

In the Installation, it said it was deleting everything from my old OS, and Partitioning my Hardrive... Are they all gone?

boot into ubuntu, go Applications > Accessories > Terminal. Run ```
sudo fdisk -l
```That is a lowercase L in -l

Post back the output of that command.

---

