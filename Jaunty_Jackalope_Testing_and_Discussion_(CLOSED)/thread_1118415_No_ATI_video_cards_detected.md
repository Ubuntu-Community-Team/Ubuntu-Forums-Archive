---
title: "No ATI video cards detected?"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sansa dude on 2009-04-07
i know i have an ATI Radeon x1650 pro video card installed, but ATI Catalyst Control Center doesn't detect it. the card works fine and gives me my video and my monitor is detected ok. it just says there is no ATI cards installed.

i also ran

```
aticonfig
```and it came up saying no cards were installed. is there a fix for this?

---

### Post by krazyd on 2009-04-07
AMD have moved support for your card completely to the open source driver. This means that the fglrx included in Jaunty will not support your card. It should work out of the box.

Do you have a specific reason for wanting to use fglrx?

---

### Post by sansa dude on 2009-04-07
> **krazyd said:**
> AMD have moved support for your card completely to the open source driver. This means that the fglrx included in Jaunty will not support your card. It should work out of the box.

Do you have a specific reason for wanting to use fglrx?
assuming fglrx is ATI Catalyst Control Center i just had it on my windows system and my previous Ubuntu system so i assumed it would work for 9.04. so where is the open source driver that is available for my card?

---

### Post by Lorenz on 2009-04-07
The reason for us ATI users to use fglrx would be to enable compiz, amongst other reasons. I have not yet been successful with the open source drivers either, is there an easy way to install (like sudo aptitude install ati-opensource-drivers for example)?.

---

### Post by kzip on 2009-04-07
I'm using the opensource drivers on my Thinkpad T60 with an X1300 ATI card and compiz works fine (including rotating cube effects etc).

"xserver-xorg-video-ati" and "xserver-xorg-video-radeon" are the two packages.

glxgears runs at 1250 fps (which I know people say isn't a benchmark but there you go).

---

### Post by krazyd on 2009-04-07
> **sansa dude said:**
> assuming fglrx is ATI Catalyst Control Center i just had it on my windows system and my previous Ubuntu system so i assumed it would work for 9.04. so where is the open source driver that is available for my card?
It's installed by default. Try something 3D! :)
> **Lorenz said:**
> The reason for us ATI users to use fglrx would be to enable compiz, amongst other reasons. I have not yet been successful with the open source drivers either, is there an easy way to install (like sudo aptitude install ati-opensource-drivers for example)?.As above, they're installed by default. If your card is a Radeon HD 2xxx, 3xxx or 4xxx then 3D is not fully supported by the open source drivers (yet ;)). fglrx works though.

---

### Post by Lorenz on 2009-04-07
> **kzip said:**
> I'm using the opensource drivers on my Thinkpad T60 with an X1300 ATI card and compiz works fine (including rotating cube effects etc).

"xserver-xorg-video-ati" and "xserver-xorg-video-radeon" are the two packages.

glxgears runs at 1250 fps (which I know people say isn't a benchmark but there you go).

Oh, thank you very much indeed! I got exactly the same machine, so that will help :)

Edit: As the above poster mentioned, those drivers were indeed already installed and they do work fine with effects enabled. I'm sorry for the confusions, this didn't work during the Alpha afaik.

---

### Post by sansa dude on 2009-04-09
i had compiz working fine on my card but when im not sure if its my card or jaunty but my computer wont boot now with the right video settings

---

