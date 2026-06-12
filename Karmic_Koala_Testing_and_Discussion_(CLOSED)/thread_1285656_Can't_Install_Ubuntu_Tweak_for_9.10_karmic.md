---
title: "Can't Install Ubuntu Tweak for 9.10 karmic"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theetechkid on 2009-10-08
I downloaded the package for ubuntu tweak 0.4.9.1-1 karmic1_i386.deb. But when i go to install the package it displays this message:

dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor

And by the way i just got ubuntu so i am very new to this. If you could bare with me im still learning.

---

### Post by Giwex on 2009-10-08
This was a bug in Karmic (it was impossible to install any deb package using the GUI) but was solved with later updates. So the question is "did you fully update your karmic installation"?
It the answer is positive you can install it using the terminal and typing 
```
sudo dpkg -i packagename
```

But, being a new kid on the block wasn't better to install the 9.04 version and make all the experiments you need to while awaiting the final version of 9.10? :KS

---

### Post by clhsharky on 2009-10-08
Ubuntu Tweak 0.4.9.1 is in the karmic repositories. Ive had no problems with it.

---

### Post by wilee-nilee on 2009-10-08
I always use the ppa version, [https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa](https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa)  If you are not familiar with how to add the key let us know.

---

