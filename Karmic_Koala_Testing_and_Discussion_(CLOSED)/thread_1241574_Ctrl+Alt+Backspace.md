---
title: "Ctrl+Alt+Backspace"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Partyboi2 on 2009-08-16
Hi, I have enable Ctrl+Alt+Backspace (key sequence to kill xserver), but it only works when the "Keyboard Preferences" window is open. If I try when the "Keyboard Preferences" window is closed it does nothing.
Is anyone else having this problem or know of a workaround?

---

### Post by Barrucadu on 2009-08-16
How did you enable it? In your xorg.conf?

---

### Post by Harper45 on 2009-08-16
whats its function??

---

### Post by Partyboi2 on 2009-08-16
I enabled it by going to System>Pref>Keyboard then to Layouts>Layout Options>Key sequence to kill xserver.

---

### Post by WinterWeaver on 2009-08-16
doesn't exist anymore.... in 9.04 it's >> Alt + SysRq + K

---

### Post by Partyboi2 on 2009-08-16
> **Harper45 said:**
> whats its function??
Its function is to kill the xserver and take you back to the login screen.

---

### Post by Partyboi2 on 2009-08-16
> **WinterWeaver said:**
> doesn't exist anymore.... in 9.04 it's >> Alt + SysRq + K
You can enable it in 9.04 by using
```
dontzap --disable
```
But this is not available in Karmic. 
In Karmic you can enable it by the steps I took. (well at least it is meant to work)

---

### Post by WinterWeaver on 2009-08-16
/Facepalm

I shoulda read the thread category (Karmic...) I just saw the thread on the homepage, clicked and replied lol

sorry

---

### Post by MacUntu on 2009-08-16
Working fine here. Do you have the DontZap thing in your xorg.conf? I'll remove it and try again.

Edit: Nope, doesn't make a difference if the xorg.conf entry is there or not - working fine.

---

### Post by Partyboi2 on 2009-08-16
> **WinterWeaver said:**
> /Facepalm

I shoulda read the thread category (Karmic...) I just saw the thread on the homepage, clicked and replied lol

sorry
:lolflag:  no probs!


@MacUntu
No I don't have it in my xorg.conf.

---

