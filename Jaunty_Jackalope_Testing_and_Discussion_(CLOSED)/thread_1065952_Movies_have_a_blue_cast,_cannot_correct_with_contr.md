---
title: "Movies have a blue cast, cannot correct with controls"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-02-10
Any fix?

---

### Post by taavikko on 2009-02-10
> **philinux said:**
> Any fix?

While using X player to view?!?

First suggestion is: turn off compiz.

---

### Post by philinux on 2009-02-10
All players were doing it. Compiz is off.

Get this I opened nvidia x server settings, didn't change anything, checked if everything ok, quit. Then tried to view again and it's fixed. Weird.

---

### Post by taavikko on 2009-02-10
> **philinux said:**
> 
Get this I opened nvidia x server settings, didn't change anything, checked if everything ok, quit. Then tried to view again and it's fixed. Weird.

Have you changed previously any setting in nvidia-settings?

If yes, those changes don't take effect after reboot, unless starting nvidia-settings once.

---

### Post by dr_kabuto on 2009-02-10
Hi,
maybe you are affected by this bug: [https://bugs.launchpad.net/bugs/184440](https://bugs.launchpad.net/bugs/184440)

---

### Post by philinux on 2009-02-10
> **taavikko said:**
> Have you changed previously any setting in nvidia-settings?

If yes, those changes don't take effect after reboot, unless starting nvidia-settings once.

All default settings.

---

### Post by RIchard James13 on 2009-02-11
I had this problem with Intrepid when I upgraded my video card to a new Nvidia. My solution was that in the media player you need to rotate the colours. It is a Nvidia bug or something.

In Totem go Edit->Preferences

In the Preferences dialog select the Display tab

Try changing the Hue slider all the way to the left. Experiment until the colour looks correct.

---

### Post by Nullack on 2009-02-11
Yes Richard its an nvidia driver bug. Open totem and slide the hue all the way to the left. Extra points for going over to the nvnews forum in the linux section and starting a thread complaining about this bug in their drivers!!!! :)

---

### Post by philinux on 2009-02-11
It's all fixed for me. All I did was check the settings in "nvidia x server settings".

---

