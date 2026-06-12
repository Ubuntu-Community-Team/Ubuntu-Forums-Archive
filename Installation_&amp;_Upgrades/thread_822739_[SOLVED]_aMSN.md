---
title: "[SOLVED] aMSN"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by talking Llama on 2008-06-08
I need a clear step-by-step, ultimate noob nothing-can-go-wrong guide to installing the latest version of aMSN on Hardy Heron 8.04 Ubuntu. I've got it working on my desktop as it just appeared in the add/removes programs section but my laptop is giving me trouble. Thanks.

---

### Post by unicorn_2003_1 on 2008-06-08
What trouble your laptop is giving you? Since it works fine on your desktop, what's so different about the laptop?

---

### Post by talking Llama on 2008-06-08
When I added it on my dekstop all I did was tick the box in add/remove programs, its just plain not in the add/remove programs section of the laptop's ubuntu.

---

### Post by lswest on 2008-06-08
go to system-->administration-->software sources, make sure the first 4 boxes are ticked (on the main tab) then do:
```
sudo apt-get update
sudo apt-get install amsn
``` in the terminal

---

### Post by talking Llama on 2008-06-08
Ah man thank you so much! This has worked perfectly! Got it all working great now. Thank you so much for your help! :D

---

### Post by lswest on 2008-06-09
Haha, no problem, glad I was able to help.  Thanks for the thanks.

---

