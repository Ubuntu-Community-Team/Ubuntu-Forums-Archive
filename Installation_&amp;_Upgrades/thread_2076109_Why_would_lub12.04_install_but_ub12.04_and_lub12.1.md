---
title: "Why would lub12.04 install but ub12.04 and lub12.10 fail?"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by elpidiovaldez5 on 2012-10-25
I am using an Ivy Bridge 3450s processor with Intel Graphics. 

Lubuntu 12.04 installs like a dream, but I cannot install Ubuntu 12.04 or Lubuntu 12.10.  Any ideas what the problem would be ?

I tried the nomodeset parameter as suggested by googling.  It did not help.

---

### Post by dino99 on 2012-10-25
"cannot install " , ok but what that means in details ?

---

### Post by elpidiovaldez5 on 2012-10-27
ub12.04 and lub12.10 cannot install because they cannot even boot from a USB memory.  Either the screen prints a mass of white text on a black backround with a mass of errors including reference to null pointer, not being able to mount devices and kernel panics, or it gets to the blue Lubuntu screen with progress dots and just hangs silently.  Can't print or store any of the text because computer is dead to the world.  All this is odd as lub12.04 boots and installs without a hitch.

I have also discovered that lub12.04 only boots with the 3.2.0-23-generic kernel. It crashes and burns with 3.2.0-32-generic and 3.2.0-32-generic pae.  I believe it is something to do with ivy-bridge architecture or Intel graphics. I use Intel 3450s processor.

---

