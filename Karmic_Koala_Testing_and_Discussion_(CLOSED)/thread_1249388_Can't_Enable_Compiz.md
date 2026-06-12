---
title: "Can't Enable Compiz"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alligoodw on 2009-08-25
When I try and enable Compiz, I get a message that there is a searching for drivers and then the message, "Can't enable Compiz."  I have a Nvidia graphics card in my HP Pavilion dv6000 laptop.  Is there any way around this problem?

---

### Post by simmeson on 2009-08-25
Do you have the appropriate driver installed?

---

### Post by alligoodw on 2009-08-25
Apparently not.  I'm just not sure what drivers is needed to enable Compiz.

Any suggestions?

---

### Post by taavikko on 2009-08-25
> **alligoodw said:**
> Apparently not.  I'm just not sure what drivers is needed to enable Compiz.

Any suggestions?

That depends on what card is inside the laptop.
GF6-> uses nvidia-185
below is the legacy drivers

---

### Post by alligoodw on 2009-08-25
I have a Nvidia graphics card in my laptop (HP pavilion dv6000).

---

### Post by taavikko on 2009-08-25
> **alligoodw said:**
> I have a Nvidia graphics card in my laptop (HP pavilion dv6000).

that still doesn't say anything. The model number is the one we're after.
but most probaply it's the newer chipsets.

Install "nvidia-glx-185" and edit xorg.conf to include {Driver "nvidia"}

---

### Post by anders_c_ on 2009-08-25
i have to kill metacity before starting compiz everytime i boot.

in a terminal:
killall metacity
compiz &

you could try that.

---

### Post by JohnJackson on 2009-08-25
I have the same problem using the appearance dialog.

Alt+F2 and typing in compiz works though.

---

