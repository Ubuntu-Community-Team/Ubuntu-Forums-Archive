---
title: "Metacity auto composite switch on?"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by forcecore on 2010-04-11
Why Metacity do not automatically kick in when Compiz is turned off, i have to manually activate from gconf? is that meant to be this way for technical reasons or?. I use Metacity because i do not need more just a transparent effects and minimal effects but no more. It just a question why it works this way, no pressure.

Metacity is ok even with vesa on old pc with no graphics driver available.

---

### Post by drs305 on 2010-04-11
I don't use compiz or metacity's compositing so the issue isn't one I pay much attention to. It seems to me if you are going to turn off Compiz then it's logical to turn it *all* off. 

If you want compositing back, you can easily make a shortcut from the gconf-setting:
```
gconftool-2 --type bool --set /apps/metacity/general/compositing_manager true

```

JMO

---

### Post by uBeer on 2010-04-11
It seems that Ubuntu wants to have compositing (or at least compiz) enabled by default on hardware that supports it. It checks to see if the hardware is capable or not and then activates compiz or falls back to metacity (non-composited). Before it falls back to metacity non-composited there could be a check to see if the card is good enough for the compositing feature of metacity.

That check to see if your hardware/software is able to handle metacity compositing/xrender is quite hard to do I think, because most cards can handle it in theory (it uses Xrender I believe), but not all cards can deliver nice performance, especially on really old devices. It also depends on the drivers. The nv driver from Nvidia for example is not really capable of xrender stuff, so there you'll notice that moving windows around isn't any fun... (on the side: I'm terrible happy that nouveau does handle xrender :))

So in order to make such a check you'll have to test/specify quite a lot of cards that will be able to run it.
But that is only what I believe, maybe there is some easier way to verify certain requirements.

---

