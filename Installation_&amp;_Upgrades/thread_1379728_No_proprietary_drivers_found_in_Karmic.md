---
title: "No proprietary drivers found in Karmic"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by phillytomcat on 2010-01-12
HI, I downloaded the wubi version of karmic kaola and I am trying to get ubuntu 9.10 to find my driver for wireless internet. I go to system>administration>hardware drivers.
When I click on the command which finds the drivers, I get no proprietary hardware is in use. How do I get ubuntu to recognize drivers?

---

### Post by MelDJ on 2010-01-13
what is your wifi card? 
most probably you will have to get it from the vendor's website (download from the computer you are using now then install in ubuntu)

---

### Post by howefield on 2010-01-13
If you have just installed, try opening a terminal and typing

```
sudo apt-get update
```

Then try again for the drivers.

---

