---
title: "scrolling does not stop"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by swissinvestor on 2012-07-30
I suddenly have a strange problem, I guess after an update:

I cannot stop scrolling, it automatically scrolls all the way down an I am unable to stop it. It applies to Firefox, Chromium and Evolution mail (here it automatically scrolls down to the end of my numerous inboxes - I cannot stop it at the top of my mailbox list.It basically renders the computer unusable.

Any idea what could cause this strange behaviour?

Ubuntu 12.04 64-bit with Evolution mail

---

### Post by swissinvestor on 2012-07-30
as suddenly as it came it is gone. I have no clue what caused this problem, but it does not exist anymore.

---

### Post by TheFu on 2012-07-30
**3 ideas if this happens again:**
* unplug and replug the mouse. Probably best for USB mice.
* restart the mouse driver (your mouse driver might be different)
```
sudo modprobe -r psmouse
sudo modprobe psmouse;

```* shutdown the system to complete power off, wait 5 seconds, boot. This resets the electrical connections to the mouse. Probably for ps2 mice.

---

### Post by swissinvestor on 2012-08-02
Thank you!


> **TheFu said:**
> **3 ideas if this happens again:**
* unplug and replug the mouse. Probably best for USB mice.
* restart the mouse driver (your mouse driver might be different)
```
sudo modprobe -r psmouse
sudo modprobe psmouse;

```* shutdown the system to complete power off, wait 5 seconds, boot. This resets the electrical connections to the mouse. Probably for ps2 mice.

---

