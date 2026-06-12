---
title: "Ubuntu Printers No Showing in Wine"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lcohen999 on 2008-10-27
I have noticed an interesting bug...

For some reason, none of my Ubuntu printers are showing up in any wine bottle.

This occurs with the 1.0.1 wine in the ubuntu repos as well as 1.1.7 directly from Wine.

Any thoughts?

---

### Post by timpalpant on 2008-10-27
I've been trying to figure it out for a couple of days now (since 1.1.7 came out). I've had it happen once before with a WINE update.

Anyone have any ideas?

---

### Post by timpalpant on 2008-10-28
Found the answer, a missing 32-bit libcups dependency:

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/289448](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/289448)

Note: I had to reinstall wine completely and blank my ~/.wine directory to get printers back. Also, v1.1.7 from the Wine repos does NOT work still (which is frustrating). I recommend backing up your ~/.wine directory once you get a working install; you can then always revert to 1.0.1 and that configuration.

---

