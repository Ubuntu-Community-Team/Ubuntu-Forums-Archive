---
title: "Mistake with WIFI"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by koullel on 2010-06-28
Hi,
I'm sorry, my english is not too well. I install ubuntu 10.04 on my Toshiba satelitte L550 13U but my wifi don't work. It's work just for less 20 seconds and i don't know why. Please someone can give me solution to my problem?
Thank you to everybody.

---

### Post by quixote on 2010-06-29
Well, dumb question, but have you tried System > Administration > Hardware Drivers and see if it recommends some proprietary driver?  Sometimes that's enough to get it working.

If not, can you tell us exactly which wifi card you have?  If you don't know, open a terminal (Applications > Accessories > Terminal) and type```
lspci | grep 'Network'
```(That's case sensitive.)

---

