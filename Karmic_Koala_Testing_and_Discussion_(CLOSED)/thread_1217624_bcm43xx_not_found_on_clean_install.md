---
title: "bcm43xx not found on clean install"
date: 2009-07-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mudi on 2009-07-19
Hi,

The driver for a bcm43xx card (on a Acer Aspire One) recognized perfectly in Jaunty does not load or even appear to be available in repos on Karmic Alpha 2.  As an interesting note, it did work when I upgraded from Jaunty to Karmic but on fresh install it did not work.

Has anyone else run into this?  Am I not installing the right packages?  Does a bug need to be filed?

(It certainly isn't all bad though... the builtin mic on the aspire one is finally supported effortlessly!)

---

### Post by nanog on 2009-07-19
I think its been deprecated. 

Try:  

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by mudi on 2009-07-19
d'oh!  Yup that's the one.  Works great now.  Is that driver going to be a little more accessible in the final release?  Would be great if you didn't have to get to a wired connection to install it...

---

### Post by Slug71 on 2009-07-20
Had to do the same thing. Since the 2.6.31 Kernel though my card is turned off be default. Have to turn it on manually at start up.

---

