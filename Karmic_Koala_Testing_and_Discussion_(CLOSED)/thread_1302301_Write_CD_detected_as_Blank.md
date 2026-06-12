---
title: "Write CD detected as Blank"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ybytyruzu on 2009-10-26
Hi, I have 3 laptops, one with 8.04, another with 9.04 and one with Karmic.
The one with 8.04 detected my CD with the files on it but 9.04 and 9.10 mount as blank CD. Any ideas?

Tks

---

### Post by hanzomon4 on 2009-10-27
Same happens here on occasion... file a bug I'll confirm it

---

### Post by hanzomon4 on 2009-10-27
I actually [filed a similar bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456979")... could you pop a cd in and then run dmesg in a terminal?

---

### Post by ybytyruzu on 2009-10-27
Hi, ok, here is my dmesg. Another problem, Brasero on Karmic can't burn CDs, error: unable to fixating. Here is my brasero log too.

---

### Post by buzzmandt on 2009-10-27
Mine does the same thing. it also does it in k3b.  I haven't been able to burn a cd in a while but I thought it was the burner on my laptop going out.

---

### Post by ybytyruzu on 2009-10-27
Is not hardware issue because I try now with Hardy on another partition and brasero and k3b burn without problem

---

### Post by philinux on 2009-10-27
> **buzzmandt said:**
> Mine does the same thing. it also does it in k3b.  I haven't been able to burn a cd in a while but I thought it was the burner on my laptop going out.

This must be hardware related as I burnt the Karmic rc yesterday with k3b to a cdrw, and it actually verified the data for the first time ever.

Mines an Optiarc AD-5200A

---

### Post by buzzmandt on 2009-10-27
I will try other options, and try the verify as ive never had verify work either lol.  I'll keep poking

---

