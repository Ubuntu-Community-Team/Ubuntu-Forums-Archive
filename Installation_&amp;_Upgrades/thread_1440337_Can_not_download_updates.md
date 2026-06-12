---
title: "Can not download updates"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by fargas43 on 2010-03-27
Update Manager comes up with 247 downloads, but when I hit Install Update I get a white screen and nothing happens. I have just installed 9.10.  Please help.

---

### Post by jerrrys on 2010-03-27
try this...open up a terminal (in accessories) and enter:

sudo apt-get update

and if that works, follow with:

sudo apt-get install update

---

### Post by dimoftheyard on 2010-03-27
I think the second one should have been:

sudo apt-get upgrade

---

### Post by jerrrys on 2010-03-27
oops

---

### Post by fargas43 on 2010-03-29
> **jerrrys said:**
> try this...open up a terminal (in accessories) and enter:
 
sudo apt-get update
 
and if that works, follow with:
 
sudo apt-get install update
Thanks for help. However when entering terminal I get the same 3" X 3" white screen that you can do nothing with (can not enter anything). Thanks again well keep checking

---

### Post by dimoftheyard on 2010-03-31
Does your screen turn white when you enter these commands (if so, after which one?) or immediately after starting the terminal? I didn't quite understand your explanation.
Also: Is the internet connection working?

---

