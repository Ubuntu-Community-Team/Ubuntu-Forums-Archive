---
title: "Anyone else getting huge graphical slowdowns?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FatalChaos on 2009-10-04
Today I started getting huge graphical slowdowns on my laptop with karmic on it, and I can't enable desktop effects either (they were enabled before). Now, it just says "searching for available drivers" and then says desktop effects can't be enabled. I have an INTEL 945GM integrated graphics card in a T61 Thinkpad. Someone else thought the problems are related to gnome-do, but I uninstalled gnome do and the problems persist. Has anyone else been getting these problems?

---

### Post by Aearenda on 2009-10-04
It might be the same as described in [this thread]("http://ubuntuforums.org/showthread.php?t=1281866").

---

### Post by Regenweald on 2009-10-04
I suggest you turn on metacity compositing. Closer we get to Gnome 2.30 the less compiz will work.

---

### Post by pressureman on 2009-10-04
You might be experiencing this [https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/430876](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/430876)

---

### Post by FatalChaos on 2009-10-04
I tried fixes listed in the threads above which didn't seem to fix it, but an apt-get update fixed it, although I still one of the fixes (something involving a sleep flag on the kernel?), but hopefully this means the update fixed everything.

---

