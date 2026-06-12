---
title: "Live cd won't boot"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-02-23
I tried using the daily Live CD from Feb 22/10 yesterday and it wouldn't boot. Normally in a case like that I'd just select safe graphics mode, but that option is no longer available when pressing F4. Now if you have the problem of getting a black screen, try F6 and select nomodset. See bug #[lpbug]525966[/lpbug]

---

### Post by wilee-nilee on 2010-02-23
I have better response with these daily releases by loading a thumb.

---

### Post by cristianrosa on 2010-02-26
I just tried the Alpha3 LiveCD from a USB and i have exactly the same problem. After selecting the "Try without installing" option, it sets the video mode and the screen goes black. After waiting a while I tried to VT switch with no success, but finally I just pressed the enter key and the screen blinked again, and I got to the GDB login screen...from there on everything works.
I'm on a Dell Precision M90, that has a Quadro FX1500 (G71), I assume that is related to the nouveau driver.
Any clues?

---

