---
title: "Wrong video Card"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by Schiavonske1013 on 2007-06-21
It seems like Ubuntu is detecting my onboard video controller instead of the one in my PCI slot. It gives me X Server errors, and when I try to reconfigure it, it will only see my Onboard Video, not the PCI Card.

---

### Post by empthollow on 2007-06-21
the first thing i would do is try disabling the onboard video card in the bios settings.  if you are trying to use dual monitor settings i do have some expierence in this area and may be able to help with that too. i think xorg by default configures one video card.  also if you could post the output of 
```
lspci 
```
this shows all devices, it may be there and xorg is not finding it as default.

---

### Post by Schiavonske1013 on 2007-06-21
where would i type in the code?

and no, i am only on 1 monitor. my stupid dell BIOS doesn't let me turn off the onboard video

---

### Post by empthollow on 2007-06-21
go to Applications -> accessories -> terminal

---

### Post by Schiavonske1013 on 2007-06-22
but i cant boot into ubuntu, it gives me x server errors, that is what started this whole thing

---

### Post by empthollow on 2007-06-22
oh, i see, does it list the error messages and do they come up when you boot from hard drive, cd, or both.  the other thing to consider is if the x-server is giving the errors your system is probably up and running and you could do ctrl+alt+f2 to get a command line login and run some commands there.  also your motherboard may have a jumper that will disable onboard video.  it would be near the onboard video card and some kind of sensable label. good luck let me know what happens.

---

