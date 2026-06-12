---
title: "Changed Screen Resolution, can't read ANYTHING"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Kuriyaki on 2008-03-03
I changed the resolution since I have a Dell Widescreen 22" from the current 800x600 to 1920x1250 I believe...and ever since then I can't read anything on the screen!It's one huge mess. I can't read anything! Any idea how to revert back to 800x600? Or something readable? Thanks. 

Even the logon screen is a big mess..

I'm using the latest Ubuntu.

---

### Post by taurus on 2008-03-03
What graphic card do you have and have you installed a driver for it?

Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, you can either reboot or get back to GUI login screen, <Alt>F7, and restart X with <Ctrl><Alt>Backspace.

---

### Post by Pumalite on 2008-03-03
What's your video card? Did you enable restricted Drivers (if you have them)?
You can go to System>Preferences>Screen Resolution and change back.

---

### Post by Kuriyaki on 2008-03-03
I have the 8800gt XFX Graphics Card...using dual monitor. :) 

I'll try out the previous shortcuts...to see if I can get it to work. Since I can't absolutely see ANYTHING. Log On screen...nothing.

---

### Post by Pumalite on 2008-03-03
Did you try taurus suggestion?

---

### Post by Eric Boring on 2008-04-25
Hey, Just wanted to say thanks! I searched and found this answer and it saved my butt. I could not read a word on my screen until I followed these directions. Awesome.
-E

---

