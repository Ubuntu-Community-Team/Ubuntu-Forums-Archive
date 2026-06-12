---
title: "SiS Mirage M672 graphics"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Gina on 2008-10-16
I'm looking at replacing my dead laptop with a new one and checking compatibility.  For one on my list, I've just been checking the graphics - SiS Mirage M672 - and the results of my searches are not good.  Does anyone know it there is a driver for this graphics chipset for Ubuntu?  The laptop is a Packard Bell MX37-S-200.  In most respects this seems good value at £300 (300 UK Pounds) - I cannot afford much more than that.

Alternatively, does anyone know of a list/database of Linux compatible hardware?  I'm sure I've seen mention of this before but I can't seem to find it.

---

### Post by psyke83 on 2008-10-16
> **Gina said:**
> I'm looking at replacing my dead laptop with a new one and checking compatibility.  For one on my list, I've just been checking the graphics - SiS Mirage M672 - and the results of my searches are not good.  Does anyone know it there is a driver for this graphics chipset for Ubuntu?  The laptop is a Packard Bell MX37-S-200.  In most respects this seems good value at £300 (300 UK Pounds) - I cannot afford much more than that.

Alternatively, does anyone know of a list/database of Linux compatible hardware?  I'm sure I've seen mention of this before but I can't seem to find it.

If you're looking for a budget laptop, I highly recommend something with Intel integrated graphics. It is beyond a doubt the best-supported graphics chipset on Linux, whereas SiS support is spotty at best (e.g., don't expect 3D/compiz at all).

As for databases, you can check a site like [Linux on Laptops]("http://www.linux-laptop.net/"), or on the Ubuntu [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam"). Alternatively, if you see a laptop that you're interested, simply search these forums, or google linux+laptop model.

---

### Post by Gina on 2008-10-16
Thank you :) I think that laptop may not be such a good choice and I'll look at your suggestions.

---

### Post by INAPPROPRIATE_USERNAME on 2008-10-24
Having bought the exact laptop you were considering (while it was on sale for £300 at Currys) I would advise against. Hardware issues with linux:

Wireless card doesn't work on install - you need to install the latest snapshots of madwifi_hal (from source) to get it working. This was true of both Ubuntu & openSuse. Apparently you can get it working using the windoze drivers & ndiswrapper - didn't try but people have reported success.

Sound card doesn't work either - you'll need to edit alsa-conf adding options snd-hda-intel model=lenovo and, if you want headphones to work properly, position_fix=1. (That confused the hell out of me - got speakers working with model=hp, took many hours of messing about to even consider changing the model when the most intuitive choice appeared to work (no headphones with model=hp) 

openSuse did a decent job with the monitor, but to get resolution above 600x800 from Ubuntu took another manual edit.

Ok - so far just the kind of tweaks you expect to have to make to get your laptop hardware working, but the onboard SiS Mirage M672 is a different matter. With openSuse you get reasonable 2d performance from the Vesa framebuffer driver, but with Ubuntu... nada. A 2d driver is available, but when I installed it I just got psychadelic colours. While a 3d driver has been written, SiS are not making it available, nor are any of the motherboard manufacturers. Pretty poor on their part imo.

If you buy this machine, you will get - at best - poor 2d acceleration. I advise buying something else, even if it costs a few quid more.

---

