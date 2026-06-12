---
title: "[SOLVED] Firefox update made the fonts big"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2008-10-20
There was a Firefox update and after I restarted it I noticed the fonts in Firefox are really big. It's really noticeable in the awesome bar. The fonts look like a 20pt font or something. :shock: Kind of annoying. Anyone else see this?

---

### Post by jfernyhough on 2008-10-20
I haven't seen that for ages...

Check the DPI settings in about:config (layout.css.dpi). It should default to -1 which means it's detecting the DPI from the X server. You could try to set it manually to your font DPI and see if that makes any difference (or reset it back to -1).

---

### Post by mc4100 on 2008-10-20
I just applied the update ... certainly not seeing any 20pt font sizes, but the do look slightly bigger as you said in the Awesomebar (I think placebo effect, though). Try backing up and then deleting .mozilla.

---

### Post by Sslaxx on 2008-10-20
There's a good chance this and [http://ubuntuforums.org/showthread.php?t=950640](http://ubuntuforums.org/showthread.php?t=950640) are related.

---

### Post by FuturePilot on 2008-10-20
> **Sslaxx said:**
> There's a good chance this and [http://ubuntuforums.org/showthread.php?t=950640](http://ubuntuforums.org/showthread.php?t=950640) are related.

I'm not sure. This only seems to affect Firefox.

As you can see in the screenshots the font of the menubar is bigger/bolder than what my system fonts are set at. Before this update they were the same. And the fonts in the awesome bar are just plain huge. :confused:

The DPI setting in [noparse]about:config[/noparse] is still set to -1.

Edit:
Nevermind. I logged out and back in again and everything was normal. :confused:

---

