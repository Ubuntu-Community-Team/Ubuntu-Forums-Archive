---
title: "Desturcive update to fiesty?"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by wormeyman on 2007-03-23
I have a spare box that i installed fiesty on but i had edgy before and tried all kinds of weird stuff because it was my non-production machine.  So the question is now that i've upgraded to fiesty can i without burning a cd do a destructive update ala a clean install to the fiesty beta?

---

### Post by zvacet on 2007-03-24
I´m not sure but I think that you will came to beta with updates wich Ubuntu will send.

---

### Post by wormeyman on 2007-03-24
Thanks for the reply but there has to be some command i can issue isn't there?  I guess i can just waste a cd.

---

### Post by lime4x4 on 2007-03-24
this will update your current system to feisty

run from a terminal


gksu “update-manager -c -d”

---

### Post by zvacet on 2007-03-25
command is
```
update-manager -d
```

---

### Post by Onimae on 2007-03-25
I gather that you aren't asking how to do a regular update. You want a clean slate. Those commands will just update you to Feisty by installing all the Feisty packages and leaving your current system intact. As far as i know the only way to do what you're thinking about is to boot from the Feisty CD and delete your current partition from the setup and install Feisty on a new blank (or, mostly blank) partition.

**Onimae**

---

### Post by wormeyman on 2007-03-25
ok i guess i have to burn a cd not that big of a deal i guess.

---

