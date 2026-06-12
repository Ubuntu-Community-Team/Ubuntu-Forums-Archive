---
title: "gutsy not loading / installing"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Bashed on 2007-10-24
I downloaded official 7.10 and burned the iso as usual.  It boots and 5 minutes later, tells me running in low graphics mode. I click continue, it goes to a blank screen which says "running boot scripts...." and never proceeds further. I tried this again with all usb unplugged from laptop, same problem. What could be the cause?

My video is Nvidia 8400M GT with 256MB 1280x800 widescreen, 4GB memory - Core 2 Duo.

---

### Post by Sef on 2007-10-24
What drivers are you using?

---

### Post by Martje_001 on 2007-10-24
If you get the message, press CTRL + ALT + F1. Then type:
```
sudo apt-get install nvidia-glx
```

If finished, press CTRL + ALT + F7. Then press CTRL+ALT+BACKSPACE.

---

### Post by Bashed on 2007-10-24
> **Sef said:**
> What drivers are you using?

What? How would I be using ANY drivers if it is not even completing the boot process???

---

### Post by Martje_001 on 2007-10-24
See my previous post. Your using open-source drivers now, you need restricted. That's what you do (if you follow the instructions in my post).

---

### Post by Bashed on 2007-10-31
This is not working at all. I am using the official 7.10 live cd and during the boot process I still get the errors. I cannot sudo obviously without an actual password nor wget anything nor apt-get anything off the live cd DURING boot process. 

I thought Ubuntu "Just Works"???

---

