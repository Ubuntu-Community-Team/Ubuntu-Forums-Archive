---
title: "[SOLVED] CRT resolution/refresh rate issue with Gutsy Live CD (nvidia)"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by twicebjorn on 2007-11-03
**[EDIT: Solved! Not really. It seems to have sorted itself out. I tried going back to a command line, and after messing around for a bit I restarted the X server, and lo and behold I had a desktop! Not sure what happened, there, but it works, so I'm not complaining! I'll leave the post here in case it helps anyone else.]**

I just decided to scrap my Feisty partition and go for a fresh Gutsy install (also going back from 64 to 32 bit, but that's another story) when I ran into a pretty major hiccup with the Gutsy Live CD.

Everything works fine to begin with. I will write exactly what I see, in sequence:

- Live CD menu, all good, yadda yadda...
- Ubuntu logo and the back-and-forthy loading bar
- Loading bar glitches a bit, but seems okay
- Beige screen with a ticking cursor dead centre. By the size of the cursor, the resolution is reasonable
- *click!* Dead CRT!

I am guessing that the Live CD is trying to switch me into a resolution/refresh rate that my monitor can't handle. The very first time I tried it, the monitor didn't die straight away, but it did glitch like hell and make that piercing noise these old beasts make when they are running at a frequency they can't deal with. Normally I would know how to deal with this, but being that this install is coming from a read-only disk, I am really at a loss for what to do.

A Google search came up with [_>>this short article<<_]("http://techlogg.com/content/view/458/") -- it seems to describe my problem exactly.

My video card is an nvidia geforce 6800 ultra and my monitor is a big ol' Mitsubishi DiamondPro 21TX, in case anyone's wondering.

Thanks!

---

### Post by pbcartwright on 2007-11-03
install envy :
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

and let it configure your nvidia card.. worked for me:)

---

