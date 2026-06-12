---
title: "Firefox + flash site = high CPU usage"
date: 2009-10-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aero-Z on 2009-10-29
Hello,

I've notice that every time when I open a webpage with flash content my CPU usage jumps from something like 10% to 60-80%.
Any idea why it's like that or how to fix it?
I got 32bit system with flashplugin-nonfree

---

### Post by salva84 on 2009-10-29
Welcome to linux, my friend. In linux, flash usually gets 100% processor... and it will be forever... and ever... XD

---

### Post by Aero-Z on 2009-10-29
> **salva84 said:**
> Welcome to linux, my friend. In linux, flash usually gets 100% processor... and it will be forever... and ever... XD
Oh ok. Didn't know that.

---

### Post by L_V on 2009-10-29
Try to disable Desktop effects:

**kcmshell4 kwincompositing** (for KDE4)

---

### Post by philinux on 2009-10-29
My dual cores average 30% when viewing flash at normal size. This jumps to 75% when viewing full screen.

Flash is resource intensive.

---

### Post by salva84 on 2009-10-29
> **philinux said:**
> My dual cores average 30% when viewing flash at normal size. This jumps to 75% when viewing full screen.

Flash is resource intensive.


Yes, but only in Linux, not in Windows or MacOs, so...

---

### Post by philinux on 2009-10-29
This is the 64bit plugin too...

Down to adobe then.

---

### Post by mcduck on 2009-10-29
> **salva84 said:**
> Yes, but only in Linux, not in Windows or MacOs, so...

No, it is resource intensive on any OS.

If you get exceptionally low performance with Flash, it's most likely a problem related to your graphics card drivers.

---

### Post by gradinaruvasile on 2009-10-29
> **Aero-Z said:**
> Hello,

I've notice that every time when I open a webpage with flash content my CPU usage jumps from something like 10% to 60-80%.
Any idea why it's like that or how to fix it?
I got 32bit system with flashplugin-nonfree

What version of Firefox u use?
And what graphics card/ubuntu version u have?

---

### Post by philinux on 2009-10-29
> **Aero-Z said:**
> Hello,

I've notice that every time when I open a webpage with flash content my CPU usage jumps from something like 10% to 60-80%.
Any idea why it's like that or how to fix it?
I got 32bit system with flashplugin-nonfree

Try the flash block addon from mozilla. 

[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

---

### Post by philinux on 2009-10-29
> **mcduck said:**
> No, it is resource intensive on any OS.

If you get exceptionally low performance with Flash, it's most likely a problem related to your graphics card drivers.

I've solved my full screen flash "choppiness" by changing the freq scaling governor to conservative instead of ondemand. Seems to be much smoother.

---

### Post by uncleV on 2009-10-29
> **philinux said:**
> ...changing the freq scaling governor to conservative instead of ondemand.
How to do it, Phill?
Thanx.

---

### Post by philinux on 2009-10-29
> **uncleV said:**
> How to do it, Phill?
Thanx.

Right click add to panel. Select CPU Frequency Scaling Monitor.

Left click the applet to change the governor. If your processor supports this you'll be able to change it. Some people use performance when viewing flash.

---

### Post by uncleV on 2009-10-29
Thank you very much! I'll try it tonight at home.

---

