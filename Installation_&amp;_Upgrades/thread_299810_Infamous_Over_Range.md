---
title: "Infamous Over Range"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by RemmyLee on 2006-11-14
Hey everyone. I've been using ubuntu for quite some time now and recently decided to install Edgy. I was using Badger.

As you can probably guess by the title of this thread, I am unable to install due to an over range error with my monitor. I've tried both CDs in all modes to no avail.

Any ideas that anyone may have would be much appreciated.

---

### Post by ReaderRat on 2006-11-14
What kind of Monitor & Video card do you have?

---

### Post by RemmyLee on 2006-11-14
I have a 17" Sceptre LCD monitor and a Radeon 9200SE. I am guessing that the Radeon is the issue...

---

### Post by dbott67 on 2006-11-14
It's probably the refresh rate required for the LCD.  My LCD (Dell 2007 FP) runs at 60 Hz and would not run until I edited the xorg.conf file:
```
Section "Monitor"
    Identifier     "DELL 2007FP"
    [COLOR="Red"]VertRefresh     60.0 - 60.0[/COLOR]
    Option         "DPMS"
EndSection

```

You can also go to this site & plug in the settings for your monitor to get the appropriate settings: [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) or this one [http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

Then edit your xorg.cong file.  Of course, the trick is that as soon as the GUI tries to start your screen goes blank, so you need to press CTRL-F1 to get to the console.  Then type:
```
sudo nano /etc/X11/xorg.conf
```

Edit the file to include the modeline (or VertRefresh rate), save it and then press CTRL-F7 to get back to the GUI... if all goes well, you should be in business.

-Dave

---

### Post by RemmyLee on 2006-11-15
Thanks for the reply. I'm unfortunately still unable to get it. The farthest I can get on any of the CDs is the default Menu. I can escape to command line for booting, but that doesn't do me much good. I may end up reinstalling Badger and trying the painful process of upgrading my way to Dapper/Edgy.

I knew I should have kept that old CRT.

---

### Post by wpshooter on 2006-11-15
Try installing from the ALTERNATE CD.

---

