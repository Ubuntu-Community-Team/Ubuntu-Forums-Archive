---
title: "I have no icons in 12.04 fresh install"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by sirjoe25 on 2012-07-17
When I hover the mouse over where the icons should be (left side), I see arrows with the name of icons.  I can still click them and use ubuntu, but can't sort what is wrong.  I suspect it's with my graphics card?  any idea for a first time user.

---

### Post by jmfal on 2012-07-17
Welcome to Ubuntu

In top right corner is icon (looks like a gear) click on it >> system settings>> my unity
 check settings for launcher >>set to display

---

### Post by sirjoe25 on 2012-07-17
I have tried just about every option in myunity.  And still no luck.  Here is a screenshot of my desktop

---

### Post by sirjoe25 on 2012-07-17
So I poked around a bit and found some more info.  I restarted and booted in recovery mode.  I executed a dpkg (repair broken packages) and restarted into normal mode.  The icons now showed.  But, if I restart again, the icons are missing again.  Any ideas?

---

### Post by Finnicella on 2012-07-17
Hi, I'm a beginner, but if nothingelse work, you can trie with:
```
unity --reset-icons
```
Bye

---

### Post by sirjoe25 on 2012-07-17
no luck with the reset.  There were a bunch of warnings and errors.  Compiz (animation) error animation settings mismatch in "animation selection"... and other errors.

I think I am going to try to re-install and see what happens?

---

### Post by Finnicella on 2012-07-18
Before re-installing try only:
```
unity --reset
```
Bye

---

