---
title: "Blurry flash elements"
date: 2008-08-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by andrek on 2008-08-02
I'm running up-to-date intrepid ibex alpha 3. I've just set up opendns ( with inadyn so it updates IP every time I boot into Ubuntu ) but I noticed something odd. The fonts showing on stats graph are blurry, so are these in Flash's settings. Is any of you guys experiencing this issue?

Screenshot : [[img]http://xs130.xs.to/xs130/08316/screenshot-1955.png.xs.jpg[/img]](http://xs130.xs.to/xs130/08316/screenshot-1955.png)

It does not happen on, for example, YouTube - everything seems to be OK.

---

### Post by psyke83 on 2008-08-03
> **andrek said:**
> I'm running up-to-date intrepid ibex alpha 3. I've just set up opendns ( with inadyn so it updates IP every time I boot into Ubuntu ) but I noticed something odd. The fonts showing on stats graph are blurry, so are these in Flash's settings. Is any of you guys experiencing this issue?

Screenshot : [[img]http://xs130.xs.to/xs130/08316/screenshot-1955.png.xs.jpg[/img]](http://xs130.xs.to/xs130/08316/screenshot-1955.png)

It does not happen on, for example, YouTube - everything seems to be OK.

Flash 10 beta 2 seems to apply bilinear filtering for some content but not others, and this behaviour is new as of beta 2. The latest version also uses a lot of CPU for certain kinds of flash content - and such content is glacially slow on my system.

Aside from that, Firefox has a serious bug in "windowless mode" (which is now used by Flash 10 beta 2). If you're on 32bit Ubuntu, you may want to see [this]("http://ubuntuforums.org/showpost.php?p=5472028&postcount=33") post to fix crashing issues. It won't help with high CPU usage or the filtering as you see it, though.

---

