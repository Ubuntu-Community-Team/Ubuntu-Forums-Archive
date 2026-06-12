---
title: "Where'd my display go?!"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by bryngeo on 2007-07-05
Installed nvidia geforce, restarted, bsod (black). Please advise on uninstalling video driver without being able to see...

---

### Post by dreadlord_chris on 2007-07-05
> **bryngeo said:**
> Installed nvidia geforce, restarted, bsod (black). Please advise on uninstalling video driver without being able to see...

How did you install the drivers and which ones were they?

The following is a *quick-fix* that will get you back to a GUI desktop - it won't be using the NVIDIA drivers, so that will still have to be delt with.
When you get the BSOD press **Control-Alt-F1** this will bring you to a *console* - log in from there:
```

sudo dpkg-reconfigure xserver-xorg

```
When asked what driver choose **vesa**
Now, restart GNOME:
```

sudo /etc/init.d/gdm restart

```

---

### Post by bryngeo on 2007-07-05
thanks, I installed  nvidia geforce go 420, downloaded from nvidia. I then went and enabled nvidia accelerated graphics driver in restricted drivers- dumb huh?

---

### Post by dreadlord_chris on 2007-07-05
> **bryngeo said:**
> thanks, I installed  nvidia geforce go 420, downloaded from nvidia. I then went and enabled nvidia accelerated graphics driver in restricted drivers- dumb huh?

actually, just doing that *should* have worked. How, exactly, did you install the drivers you downloaded?

---

### Post by danimall on 2007-07-21
I have an HP dv6408nr notebook and I was able to get Ubuntu 6.10 to install correctly onto my computer using the live CD, but now when I try to start it up it will get to the Ubuntu loading splash screen and then just go completely blank. Is this an issue with the Nvidia drivers for my graphics card? If so then how would I work around it? I am still kind of new to linux so if you have any basic solutions then that would be great. My specs are listed below.

Microprocessor 1.8 GHz AMD Turion ™ 64 X2 Dual-Core Mobile Technology TL-56
Microprocessor Cache 512KB+512KB L2 Cache
Memory 1024 MB DDR2 System Memory (2 Dimm)
Memory Max Max supported 2048 MB
Video Graphics NVIDIA GeForce Go 6150 (UMA)
Video Memory Up to 287 MB

It probably doesn't make a difference but I am dual booting Ubuntu 6.10 and Vista.

---

### Post by upchucky on 2007-07-22
i have the go 420 card in my toshiba laptop, it need some special tweaks to make it work, google it there is a step by step, in fact i saw a step by step for the go 420 in these forums some time ago.

---

