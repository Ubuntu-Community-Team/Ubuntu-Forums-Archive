---
title: "help with su password.  It is not accepted..."
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2007-06-24
Hello :)

I have installed Ubuntu 7.04 and it seems to me that I have mixed some things in my mind.

I was under the impression that the password that the GUI is asking you eg. when you use synaptic is the SU password.
It seems that they are different.  While the password is accepted when synaptic asks for it, when I enter su in a console, the password is not accepted.

What am I doing wrong?  If I don't remember my su password is there any way to retrieve it, or reset it?

Thank you all in advance...

---

### Post by Pumalite on 2007-06-24
Try sudo.

---

### Post by Scunizi on 2007-06-24
Just to clairify.. don't use sudo as the password, use sudo in place of su.  You'll need to enter all root commands by putting sudo in the front of the command. Sudo gives temporary root privledges.

---

### Post by Nekiruhs on 2007-06-24
```
sudo su
``` is what your looking for

---

