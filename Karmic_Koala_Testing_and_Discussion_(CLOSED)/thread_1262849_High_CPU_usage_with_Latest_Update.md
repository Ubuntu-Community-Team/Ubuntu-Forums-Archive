---
title: "High CPU usage with Latest Update"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alligoodw on 2009-09-10
When I boot-up with the latest updates, I've noticed (using System Monitor) that the CPU usage is at 100%; as a result, the fan blows continuously.  What do I look for in System Monitor that will tell me which program is causing the spike?  I'm trying to remedy the situation.  

I'm enjoying the Karmic Koala testing.

---

### Post by dino99 on 2009-09-10
use htop to kill the process eating cpu power 
then, you can remove purge this package & reinstall it after.

---

### Post by jocko on 2009-09-10
> **alligoodw said:**
> When I boot-up with the latest updates, I've noticed (using System Monitor) that the CPU usage is at 100%; as a result, the fan blows continuously.  What do I look for in System Monitor that will tell me which program is causing the spike?  I'm trying to remedy the situation.  

I'm enjoying the Karmic Koala testing.
It's probably sreadahead doing it's job to optimize your boot process. It only runs after an update that affects files that needs to be read during boot. Just let it run. Once karmic is released it will not run very often.

---

### Post by Robin Nixon on 2009-09-10
I had that too and it turned out to be pulseaudio. I removed it but it keeps coming back with system updates :(

---

### Post by alligoodw on 2009-09-10
Confirmed.

---

### Post by dino99 on 2009-09-10
pulseaudio have played with my nerves some time ago too.
i finally stop these issues by removing purging everything about pulseaudio, searching hidden config files and removed them.
Then reinstalled pulseaudio, no more trouble after that.

---

