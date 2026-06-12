---
title: "Black Screen"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by LauZaIM on 2008-01-10
Hi, I recently downloaded and burned Ubuntu 7.10. My problem is that after I select a choice on the first boot screen it just goes black and stays there. However, on my laptop it works just fine and boots into Ubuntu. Whats the problem?

---

### Post by taurus on 2008-01-10
Could be due to the graphic card on your machine!  What is it anyway?

---

### Post by LauZaIM on 2008-01-10
Its an 8800GTS

---

### Post by Partyboi2 on 2008-01-10
You could try booting with nosplash
to do this when you get to the main menu press F6 and at the end of the line change ```
splash
```
to
```
nosplash
```
then press enter

---

### Post by LauZaIM on 2008-01-11
Ok, I went ahead and got the 32-bit version of Ubuntu which works fine with my hardware with the loading screen and LiveCD. I went ahead and installed it on a seperate HDD. Now, I have yet another problem. After the install I took the cd out, went into the bios and put the HDD I installed it on as first boot and disabled the rest. It boots up with an "Error loading operating system" screen. I'm getting the feeling Ubuntu just hates my system...

---

### Post by Partyboi2 on 2008-01-11
try using supergrub
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by LauZaIM on 2008-01-11
Well I managed to get everything working ok now. It was a strange fix but I tried setting the dvd drive as first boot and disabled the rest of the options and it loaded GRUB and I was able to select Ubuntu and load it fine. (And no, I didn't have the cd in the drive so it wasn't running from it.) I also can boot into Windows still. Thanks for being so quick to respond.

---

