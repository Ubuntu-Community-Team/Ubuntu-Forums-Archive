---
title: "Repair Ubuntu cause of freezing during update"
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by noob707 on 2009-08-31
Ubuntu Karmic Koala Alpha 4

I was installing a update for packages with the update manager. It was configuring the packages and almost when my laptop froze not to heat. So i can still use Ubuntu but many applications don't start or work like Update Manager, or Apperance. I tried doing sudo apt-get -f install but that didn't fix anything it just said that nothing needs to be installed or upgraded. Also when i try to launch into any of the 3 kernels, it all the same. I have an Alternate and Live CD of Karmic Koala Aplha 4. Is there anyway to restore ubuntu to a working state. Please Help.

---

### Post by Swagman on 2009-09-01
open a cli (terminal) and type

```


sudo dpkg --configure -a


```

When you try update manager and it bombs out it actually tells you this in its message.

Just copy & paste the message into a terminal

---

### Post by overdrank on 2009-09-01
Moved to Karmic Koala Testing and Discussion

---

