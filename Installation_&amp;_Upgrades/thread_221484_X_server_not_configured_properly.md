---
title: "X server not configured properly?"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by leveliv on 2006-07-23
as soon as I am done the install..of Ubuntu it looks like it's going normally but then the screen goes black and it comes to a blue screen that looks like the setup saying..: X server (your graphical interface) failed to load...would you like to view the output to detect any errors and so I say yes...and it shows me this page or writing that looks like some sort of readme file...I'm running an onboard ATI radeon 200 express chip for video...please help!!

---

### Post by tseliot on 2006-07-23
Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine


Then you might want to install ATI's proprietary driver

---

### Post by leveliv on 2006-07-23
thank yah :D that should work I don't see why not...in the setup it didn't give me a chance to configure Xserver it must do it automatically, btw where can I get the ATI proprietary driver?

---

