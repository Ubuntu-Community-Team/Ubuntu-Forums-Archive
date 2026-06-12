---
title: "Intel x3100 / 965 graphics chipset"
date: 2008-06-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by spamzilla on 2008-06-01
I read on a devs blog that this driver may be ready for Ibex, but I haven't heard anything for about 5-6 months now.

Does anyone know what the latest news is on this chipset? Will I (we) finally be able to use the proper intel driver rather than a generic driver?

Any other info would be great

Cheers

---

### Post by NineKnuckles on 2008-06-01
The only thing I've heard about this chipset is that it isn't blacklisted for compiz anymore.

---

### Post by Sockerdrickan on 2008-06-01
I don't know what 8.04 uses but when I play Half-Life my computer freezes after ~5 min

---

### Post by smartboyathome on 2008-06-01
When I play any 3D game, my comp freezes after a while as well. :(

---

### Post by spamzilla on 2008-06-01
Most games which require use of my graphics chipset won't play either. I know it's never going to be a decent graphics chipset, but it should at least work as intended. 

Lets hope the video-intel-2.3~ drivers will be a lot better than the current versions we are using.

---

### Post by Josh04 on 2008-06-01
> **smartboyathome said:**
> When I play any 3D game, my comp freezes after a while as well. :(

Have you tried turning off compiz?

---

### Post by smartboyathome on 2008-06-01
That works, but then when I try to turn compiz back on after, it sometimes freezes my comp and I have to hard restart it. :(

---

### Post by Josh04 on 2008-06-01
> **smartboyathome said:**
> That works, but then when I try to turn compiz back on after, it sometimes freezes my comp and I have to hard restart it. :(

Yeah, I don't have a fix for that one yet :P

---

### Post by andrewabc on 2008-06-02
I also hope they fix compiz better for x3000 965g
Currently with compiz enabled, xorg uses 70% CPU when scrolling in firefox and other programs.
At one point during the testing of hardy it worked perfect, but then I got an update for something and it went back to using all the CPU.

I really want compiz to be able to use AWN.

---

### Post by spamzilla on 2008-06-02
> **andrewabc said:**
> I also hope they fix compiz better for x3000 965g
Currently with compiz enabled, xorg uses 70% CPU when scrolling in firefox and other programs.
At one point during the testing of hardy it worked perfect, but then I got an update for something and it went back to using all the CPU.

I really want compiz to be able to use AWN.

I got compiz + AWN working with the x3100. Compiz is a bit glitchy though.

---

### Post by aamukahvi on 2008-06-02
> **andrewabc said:**
> I really want compiz to be able to use AWN.
You don't really *need* Compiz for that. Any compositing manager will do, for example the one in metacity. You can turn it on in gconf, /apps/metacity/general/compositing_manager .

---

### Post by andrewabc on 2008-06-02
> **spamzilla said:**
> I got compiz + AWN working with the x3100. Compiz is a bit glitchy though.
Yes compiz works normal for me in the sense that everything works. I can't use it though as it uses too much CPU. Mostly with scrolling in firefox (or opera)

> **aamukahvi said:**
> You don't really *need* Compiz for that. Any compositing manager will do, for example the one in metacity. You can turn it on in gconf, /apps/metacity/general/compositing_manager .
I tried that before (it was a window manager other than compiz) and I think it still caused xorg to use high CPU. Also caused AWN to crash a bit more.

I even switched from xorg to the other older version (I forget what it was called), but it still used up lots of CPU.

I documented my problem at
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492)

---

