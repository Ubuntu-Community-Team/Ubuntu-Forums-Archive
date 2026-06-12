---
title: "badly rendered fonts with xserver-xorg-video-ati on lucid"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kmart on 2010-03-30
Hi,

Installed lucid (beta1) on a box with a Radeon HD 4550 (RV710) video card,
connected to a Dell U2711 monitor.

The installation automatically selected the xserver-xorg-video-ati driver for
use with this card, and while it came up with the right resolution (2560x1440)
and with compiz enabled, it has two big problems:

 - The fonts are almost unintelligble as they are displayed in a very distorted
   way.

 - The DPI got computed to 96 DPI (or PPI) as opposed to 109 which is the
   correct value for this particular Dell monitor. (Images and text becomes
   much crisper with 109 than with 96.)

I have tried a few things to fix these two issues, that is:

 - Created a xorg.conf file with the correct DisplaySize value set. This
   changed the DPI value reported in the Xorg.0.log file to 109, but the
   xdpyinfo command still reports 96x96 as the DPI resolution.

 - "xrandr --dpi 109" changes the value reported by xdpyinfo to 109 but
    seems to have no effect besides that.

None of these attempts at "fixes" solved the font display problem though.

Also noticed that switching off compiz dramatically improves the display of
the fonts.

I have temporarily swithed to using the fglrx driver, as this driver does not
has the font issue as the open source driver has. But this driver also comes
up with the wrong DPI value (that is 96 DPI), and there seems to be no
apparent way of correcting this. Tried with putting the DisplaySize into the
fglrx's xorg.conf file, but ut seems like that the fglrx driver ignores this value.

Used the fglrx driver with jaunty and managed to get the correct DPI there,
because one could, with the old gdm server, specify the preferred DPI value
to the X11 driver by adding "-dpi 109" to the X11 "command lines" in the
gdm's gdm.conf configuration file. But with the new gdm server this option
seems to have gone away and we have to live with whatever the X11 driver
find for good to use as the DPI value (whether it is correct or not).

As I would very much prefer to use the open source driver, rather that the
propietary fgrlx driver (which anyway still have problems with the DPI
setting), has anyone found ways of fixing the font and dpi issues?

Maybe there are some newer releases of the driver in some PPA or something?
Any ideas?

br,
kmm

---

### Post by kmart on 2010-03-30
Hi,

Tried a little bit more here. That is that I updated the installation with the latest xorg drivers from ppa:xorg-edgers/ppa and switched back from using the fglrx driver to using the xorg driver again.

After restarting there was unfortunately no change, the fonts was rendered just as badly as with the previous driver. But this time I also noted that all edges, including borders of windows and even borders in images displayed on the screen, all had distinct "sawtooth" type of edges. This leads me to belive that this might be a problem with the combination of this monitor (Dell U2711) and the xorg driver.

Took a screendump and when viewing this screendump with the fglrx driver enabled again, the fonts and edges displayed in this screendump was just fine and as they should be.

This could mean that the xserver-xorg-video-ati driver currently does not goes well with this monitor. I will try with an another montitor as soon as possible. Should be insteresting to see how it goes then.

br,
kmm

---

### Post by ffi on 2010-03-30
I had font problems too last week and just today they got mysteriously fixed

---

### Post by kmart on 2010-03-30
Hi,

Just to follow up on my last post...

Tried with my old trusty Dell 2005FPW monitor (which I have used up until I got the U2711 one). And with this monitor the problems are gone! The fonts are crisp and clear and everything.

This probably means that we can conclude with that the Dell U2711 monitor, a relatively new model on the marked, is not yet well supported by the xorg driver in combination with the Radeon HD 4550 (RV710) card.

Could it be that the driver interprets the EDID values obtained from the monitor wrongly, possibly resulting in that wrong modelines are beeing used?
Perhaps a workaround could be to set the modeline explicitly in the xorg.conf file? Which leads me to the next question; Does anyone has modelines for 2560x1440 that I could try with? F.ex. for the Apple 27" monitor if noone has modelines for the Dell monitor. Perhaps modelines could be "extracted" from the fglrx driver somehow? Anyone knows how?

Apr. the driver, I can see from the Xorg.0.log that both the ati_drv.so and the radeon_drv.so gets loaded and from the log file it seems like that it is the radeon driver that gets used.

br,
kmm

---

