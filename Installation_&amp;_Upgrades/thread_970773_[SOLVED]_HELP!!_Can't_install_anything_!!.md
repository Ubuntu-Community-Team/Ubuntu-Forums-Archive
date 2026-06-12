---
title: "[SOLVED] HELP!! Can't install anything !!"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by redioactif on 2008-11-04
Hi
Ok.
I just moved from Windows to Linux Ubuntu and just installed it on my laptop. It apperently works great except for one thing...since I installed Java or whataver from synaptics, it won't let me install anything:
If I go to Add/Remove and choose a program for example eMeSeNe to install it, it says the following error message:

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

PLEASE HELP ME!! And it says the same thing whenever I go in Synaptics.

---

### Post by Peter09 on 2008-11-04
Part of the solution is in the error message.

Open a terminal

Applications->Accessories->terminal

and type at the prompt

```
sudo dpkg --configure -a
```

that should do it.

---

### Post by Vl@d on 2008-11-04
Hello. 

Try this on your terminal 

```
sudo dpkg --configure -a
```
 and then

```
sudo apt-get update
```
```
sudo apt-get upgrade
```.

Good luck.

---

### Post by redioactif on 2008-11-04
Thank you very much for being so fast and so clear. Sorry if the question was a litte bit stupid :D 
It works great now. 
Thanks again.

---

