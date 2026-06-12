---
title: "Fonts and flickerng"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by stephanmg on 2011-07-05
Hello everbody.  About ~ 5 days ago, there was some update for my machine, which was:  
(I'm on natty narwhal 11.04 with xubuntu) 
-~> i tried fluxbox too, same problematics.

```
x11-commons
xorg
xserver-xorg
xserver-xorg-input-all 
xserver-xorg-video-all
```After that was applied and next time started the machine:

1) Fonts look now really washy/clouded/blurred.
2) Mplayer/VLC plays a video, but: vertical bars "flackering" occurs now.

-~> Nothing else than this changed on the machine. 

My Video Card is ATI Radeon HD 5570 and i've disabled/enabled the ATI proprietary driver, but that won't help.

```
My Xorg.conf is:
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection
```Best regards,
stephan

---

### Post by dino99 on 2011-07-05
into a terminal:

sudo dpkg-reconfigure -phigh -a

---

### Post by stephanmg on 2011-07-05
okay!

what next?

btw: it didn't change a thing :(

greats

---

### Post by Toz on 2011-07-05
Can you post back the contents of the file **/var/log/Xorg.0.log**? Please post it back using the code blocks option (#).

---

### Post by stephanmg on 2011-07-05
Xorg0.log
[http://nopaste.linux-dev.org/?12569](http://nopaste.linux-dev.org/?12569)

Xorg0.log.old
[http://nopaste.linux-dev.org/?12570](http://nopaste.linux-dev.org/?12570)

maybe you can do something, would be great.

---

### Post by dino99 on 2011-07-05
> **stephanmg said:**
> okay!

what next?

btw: it didn't change a thing :(

greats

run gconf-editor and look at fonts settings

---

### Post by stephanmg on 2011-07-05
@dino:

what exactly should i search for?

---

