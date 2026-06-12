---
title: "Unable to see GUI"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by Tharbad on 2008-01-08
I'm unable to get to the Grafic User Interface (so I have only command line). 
I think it's the grafic card which is ATI Raedon X1950 Pro.
My version is Ubunto for AMD64 v7.10.

Where can I get the driver (Tell me what to write in the terminal)?

Note: I'm a begginer...

---

### Post by zvacet on 2008-01-08
```
sudo dpkg-reconfigue xserver-xorg
```

and when you come to the driver stage select** vesa** and continue with configuration.When you are done you will have elementar graphic and then you can go and search for you driver.Look in restricted manager.

---

### Post by Tharbad on 2008-01-09
what do you mean by "restricted manager"?

---

