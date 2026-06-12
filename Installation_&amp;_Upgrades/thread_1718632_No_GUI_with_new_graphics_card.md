---
title: "No GUI with new graphics card?"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by thelema.6 on 2011-03-31
Hello all. I'm attempting to install a new GPU in 10.10, however after booting through the login screen I only get a terminal-like display. I searched high and low for an explanation on how to get the GUI, but only came up with very vague or complicated answers.
My theory on how to get the GUI with the new GPU:
disable onboard graphics in BIOS during boot
reconfigure xorg after login: sudo dpkg-reconfigure -phigh xserver-xorg
Do you think this will work or will i kill my computer? :confused:

---

### Post by Dutch70 on 2011-03-31
Try this, when you get to the text area, hit (cntl+alt+F7) It should present you with a login. 
Go ahead and login as usual, then it will present you with a terminal like ubuntu@ubuntu: or whatever. 
When you get there, try typing in...
```
sudo startx
```

Then update your system...
```
sudo apt-get update && sudo apt-get upgrade
```

Hopefully that will work for you. If it doesn't and you get stuck, don't do a hard reboot. Try this instead.
 
While holding down the (alt+sys rq) keys, press R-E-I-S-U-B in order with a short pause between each key. That will reboot your system safely.

---

### Post by slooksterpsv on 2011-03-31
The one command you specified should help you to reconfigure the graphics settings (sudo dpkg-reconfigure xserver-xorg)

Other than that, what graphics card did you install? AMD or NVidia? (Still want to call it ATI, but they took off the ATI portion and just made it AMD)

---

### Post by thelema.6 on 2011-03-31
thanks guys, i'll give those a try.
i'm installing an ATI 4670

---

### Post by slooksterpsv on 2011-03-31
> **thelema.6 said:**
> thanks guys, i'll give those a try.
i'm installing an ATI 4670

Ahh, if that doesn't work, run the following (make sure you have internet connection):

```


sudo apt-get install fglrx && sudo aticonfig --initial -f


```

Then reboot.

---

