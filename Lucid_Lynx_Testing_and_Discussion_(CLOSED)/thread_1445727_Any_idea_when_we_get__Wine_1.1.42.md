---
title: "Any idea when we get  Wine 1.1.42"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ToxicBurn on 2010-04-03
I really need Wine 1.1.42 there is a bug in the current 1.1.41 that i can not use. any ideas on when the deb package will be out or can i just use Alien to convert fedoras rpm and install ?

---

### Post by woodmaster on 2010-04-03
alien can be imperfect sometimes but if it dosen't work you can always uninstall it...

---

### Post by Kazade on 2010-04-03
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

You don't need to use Alien, Wine has a PPA.

---

### Post by IanW on 2010-04-03
Not built yet. Give it a day or two. After all, it *is* Easter.
(Also, we're in Beta freeze, remember - current status shown on the PPA is "(pre-release freeze)".

[https://launchpad.net/ubuntu/+source/wine1.2]("https://launchpad.net/ubuntu/+source/wine1.2")

---

### Post by ToxicBurn on 2010-04-03
thanks for the info :)

---

### Post by homerhomer on 2010-04-07
Not the official one, but looks pretty cool 

[https://launchpad.net/~vivnet/+archive/vivnet-wine](https://launchpad.net/~vivnet/+archive/vivnet-wine)


" A compilation of wine with several feature enhancing or bug fixing patches applied. Specifically: fixes for crashing in Counter-Strike: Source and Half-Life 2: Multiplayer (freetype.patch); fix for keyboard event issues that result in repeated pressing of a key that is held down (keyevent.patch); a pulseaudio driver; OpenGL Hardware Cursor support for World of Warcraft (only hwc packages)."

---

### Post by Kazade on 2010-04-07
> **homerhomer said:**
> Not the official one, but looks pretty cool 

[https://launchpad.net/~vivnet/+archive/vivnet-wine](https://launchpad.net/~vivnet/+archive/vivnet-wine)


" A compilation of wine with several feature enhancing or bug fixing patches applied. Specifically: fixes for crashing in Counter-Strike: Source and Half-Life 2: Multiplayer (freetype.patch); fix for keyboard event issues that result in repeated pressing of a key that is held down (keyevent.patch); a pulseaudio driver; OpenGL Hardware Cursor support for World of Warcraft (only hwc packages)."

Cool? Yes and No. There are reasons those patches aren't in vanilla Wine, and it's normally because although they fix the listed programs, they probably break others. If you only wanna run one of those programs then by all means try it, but if not, just stick to the official Wine ppa.

---

