---
title: "Will this PC run Lubuntu 12.10?"
date: 2012-10-15
forum: Installation &amp; Upgrades
---

### Post by t5tu4ergj5ug9 on 2012-10-15
I'm planning to install Lubuntu 12.10 (32-bit) on the following PC. Will it work or is the hardware too old?

CPU: Intel Celeron 2.0GHz
RAM: 512MB
GPU: GeForce 4 MX 440 with AGP8x

I'm especially worried that the GPU won't have drivers. The computer is used by my parents to surf the web, so if it can play Flash video, everything is fine. Also will Lubuntu 12.10 fit on a CD or do I need to burn it to a DVD?

---

### Post by ajgreeny on 2012-10-15
> **t5tu4ergj5ug9 said:**
> I'm planning to install Lubuntu 12.10 (32-bit) on the following PC. Will it work or is the hardware too old?

CPU: Intel Celeron 2.0GHz
RAM: 512MB
GPU: GeForce 4 MX 440 with AGP8x

I'm especially worried that the GPU won't have drivers. The computer is used by my parents to surf the web, so if it can play Flash video, everything is fine. Also will Lubuntu 12.10 fit on a CD or do I need to burn it to a DVD?
It should be fine.  My only slight uncertainty is the nvidia graphic card, but I believe that should also be no problem.  Try the live CD (it will fit a CD) and if that runs OK the installed version should also be good to go.

That machine is very similar to one that I use with Lubuntu 12.04, except mine has an ATI M9000 video card.  It's no Formula One machine but it is good enough for surfing the web, using LibreOffice and a bit of video viewing etc etc.

---

### Post by t5tu4ergj5ug9 on 2012-10-15
Ok. Thanks. Lubuntu also has a Software Center like Ubuntu? Does it include Firefox and Flash Player too?

---

### Post by kalehrl on 2012-10-15
Check if your processor supports PAE.
If it doesn't, you won't be able to run 12.10.
12.04 should be fine.

---

### Post by t5tu4ergj5ug9 on 2012-10-15
How can I check that?

---

### Post by kalehrl on 2012-10-16
> cat /proc/cpuinfo | grep pae
Pae option will be highlighted if it is available for your CPU.

---

### Post by t5tu4ergj5ug9 on 2012-10-16
The PC currently has XP on it. I found from a forum that Celeron 2.3GHz supports PAE, so it's safe to assume Celeron 2.0GHz also supports it?
Another question: How easy is it to set up a wired Internet connection in Lubuntu?

---

### Post by nothingspecial on 2012-10-16
> **t5tu4ergj5ug9 said:**
> 
Another question: How easy is it to set up a wired Internet connection in Lubuntu?

You plug it in.

---

### Post by t5tu4ergj5ug9 on 2012-10-16
It's already plugged in, so it will work out-of-the-box?:lolflag:

---

### Post by nothingspecial on 2012-10-16
So long as none of the hardware is broken :D

---

