---
title: "Can only see 1/4 of the display; screen then turns in to multicoloured streaks"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grahamba on 2008-10-21
Apologies if this has been answered elsewhere, but I've failed to discover a resolution even with extensive searching!

I upgraded yesterday to Intrepid Ibex. Upon booting, a box came up to say that there was a problem with the display or the resolution - what did I want to do to resolve it? I chose the default/recommended option.

The laptop then booted fine and the login screen appeared. However, it was as though the login screen was enormous and continuing outside of my laptop display: I could only see the top-left quarter of the picture. I'm not explaining this too well: all I can think of is, if you had another monitor to the right of mine, and two underneath each of those, you'd expect the rest of the picture to be displayed on those. I was able to log in by typing my username and password and hitting return, but as the login box itself was far off the screen, I couldn't see what I was doing.

The desktop displayed in the same fashion. I opted to change the screen resolution to 1024x768, in the hope that this odd display was caused by the resolution. Upon doing so, however, the screen changed: instead of my desktop or anything familiar, I saw a multicoloured screen streaked with horizontal bars of colour. I can't explain this too well either, but I can only assume it was my graphics card's way of telling me that it didn't appreciate what I'd just done and that it couldn't display anything.

So, the situation that prevails is as such: I can see 1/4 of the login screen and I can blindly log in. Having done so, however, the screen immediately reverts to the multicoloured streaks and I can't do anything further with my laptop.

Any advice would be greatly appreciated!

Cheers,

Graham

---

### Post by nystire on 2008-10-21
What laptop are you using? What driver are you using for xorg?

---

### Post by grahamba on 2008-10-21
I'm afraid I have the deep misfortune of using a Fujitsu-Siemens Amilo Pro v2030. No idea what driver I'm using - now that I have no access to my desktop, I'm not entirely sure how to find out. Sorry!

---

### Post by nystire on 2008-10-21
According to this [http://tuxmobil.org/fujitsu_siemens_amilo_pro_v2030_linux.html](http://tuxmobil.org/fujitsu_siemens_amilo_pro_v2030_linux.html) you need to use the openchrome driver for XOrg.

I'm afraid that I'm not really sure how to install it. This thread talks about new drivers, [http://ubuntuforums.org/showthread.php?t=942402](http://ubuntuforums.org/showthread.php?t=942402) but I can't see what must be done with them.

---

### Post by shafin on 2008-10-21
at the login screen,press alt+ctrl+f1 and log in to the console. then use this to reconfigure your xserver. Hopefully it'll solve your problem
```
sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by grahamba on 2008-10-29
> **shafin said:**
> at the login screen,press alt+ctrl+f1 and log in to the console. then use this to reconfigure your xserver. Hopefully it'll solve your problem
```
sudo dpkg-reconfigure -phigh xserver-xorg

```

Thanks for your help. Unfortunately, this hasn't solved my problem. Any further suggestions would be much appreciated!

---

### Post by ddarsow on 2008-10-29
I had the exact same issue with my laptop (a DELL) and it turned out to be a bad LCD screen. DELL replaced the LCD and the inverter for free under warranty. Problem solved.
Had it not been under warranty, it would have been a $500 repair.

Anyway, it may very well be a hardware problem.

---

### Post by grahamba on 2008-10-29
> **ddarsow said:**
> I had the exact same issue with my laptop (a DELL) and it turned out to be a bad LCD screen. DELL replaced the LCD and the inverter for free under warranty. Problem solved.
Had it not been under warranty, it would have been a $500 repair.

Anyway, it may very well be a hardware problem.

Sorry to hear you had a similar issue. I'm not convinced mine is a hardware problem - the problems arose after upgrading to Ibex. Upon booting, a box came up to say that there was a problem with the display or the resolution - I think this has triggered the issue.

---

