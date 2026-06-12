---
title: "Keyboard layout switcher indicator"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ichtyandr on 2010-03-03
After todays update noticed that keyboard layout switcher indicator no longer shows which language/layout is in use. I have to click at least two times to change it as well now. Instead of letters (like US or RU) it now shows keyboard symbol only (see attached screen).
Is this a new interface feature? If so, is it possible to make this more comfortable? I tried checking /desktop/gnome/peripherals/keyboard/indicator/showFlags but thats seems to be something else or otherwise it does not work

---

### Post by Polniy on 2010-03-03
> **Ichtyandr said:**
> After todays update noticed that keyboard layout switcher indicator no longer shows which language/layout is in use. I have to click at least two times to change it as well now. Instead of letters (like US or RU) it now shows keyboard symbol only (see attached screen).
Is this a new interface feature? If so, is it possible to make this more comfortable? I tried checking /desktop/gnome/peripherals/keyboard/indicator/showFlags but thats seems to be something else or otherwise it does not work
It's a regression, of course. BTW, I'm very sad about this bug. It proves how poorly thought-out indicator approach is.

---

### Post by aethralis on 2010-03-03
I took the liberty of filing the bug using some of the text from your original post. I agree the change is annoying. 

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/531438](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/531438)

---

### Post by Ichtyandr on 2010-03-03
thanks, I joined it

---

### Post by castrojo on 2010-03-03
This is a regression and will be reverted, thanks for the bug report!

---

