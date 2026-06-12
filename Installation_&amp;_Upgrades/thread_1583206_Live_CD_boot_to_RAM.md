---
title: "Live CD boot to RAM"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by mixmastamyk on 2010-09-27
Hi, 

Been trying to get the 10.4 live cd to boot to RAM using the toram parameter but it doesn't seem to work.  Tried googling and various combos of boot params but no dice.  I haven't yet found a page that clearly states whether or not it is supported and the exact syntax.  :confused:

Unfortunately, I don't have time to rebuild the disc myself.  Also, just got a new laptop with 4GB RAM so don't worry that I might not have enough.  ;)

---

### Post by mixmastamyk on 2010-09-27
Great ... looks like I figured it out.  Not as dumb as I look I guess.

I pressed F6 and then put "toram" (no quotes) into the boot parameters just before the "--".  Did not need toram=Yes or anything like that.

```
boot:  blahblahblah...  toram --
```

Now I click on Firefox or OpenOffice and BAM! loaded.  :)

---

### Post by mixmastamyk on 2010-09-27
Would change to SOLVED but can't find a way to do it.

---

### Post by mörgæs on 2010-09-27
Thread tools -> Mark as solved.

---

### Post by mixmastamyk on 2010-10-15
Gracias.

---

### Post by cholericfun on 2010-10-15
nice little trick i didnt know before, 
will definately try that out next time i get around to use a live environment

---

