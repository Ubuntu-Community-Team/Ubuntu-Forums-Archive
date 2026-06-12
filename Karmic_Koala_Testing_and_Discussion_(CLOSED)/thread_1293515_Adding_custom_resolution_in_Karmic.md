---
title: "Adding custom resolution in Karmic?"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BadSeqtor on 2009-10-17
I have a DELL Latitude E4200 (with Intel graphics) connected to an ACER 20" external display.

Everything worked smoothly on Jaunty - i.e. the external display was identified correctly and the supported resolution (1650x) was available and could be chosen.

After upgrade to Koala the display was first not identified correctly at all (Unidentified), but now is - although the maximum resolution available is 1280x1024.

So my question is - how do I add the missing resolution manually in Koala?
Worth noting is that on the 22" DELL at work with the same resolution everything works ok.

A perhaps related(?) problem is that the top panel no longer moves to the larger display, even on the DELL where the resolution works, but stays on the laptop screen. The Cairo-dock I use moves though.

Would greatly appreciate any help. :)

---

### Post by 23meg on 2009-10-17
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

---

### Post by BadSeqtor on 2009-10-17
Thank you for the link.

I first ran;
[php]>xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 [/php]Then;
[php]>cvt 1650 1050
Modeline "1656x1050_60.00"  144.75  1656 1760 1936 2216  1050 1053 1063 1089 -hsync +vsync[/php]Then;
[php]xrandr --newmode "1656x1050_60.00"  144.75  1656 1760 1936 2216  1050 1053 1063 1089 -hsync +vsync[/php]Trying to set the resolution with --addmode fails though;
[php]xrandr --addmode VGA1 1650x1050
xrandr: cannot find mode "1650x1050"
[/php]Also tried 1656x1050, 1656x1050_60.00 with the same result.

A new run of xrandr shows the added resolutions as;
[php]TV1 disconnected (normal left inverted right x axis y axis)
  1656x1050_60.00 (0x157)  144.8MHz
        h: width  1656 start 1760 end 1936 total 2216 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1063 total 1089           clock   60.0Hz[/php]Any ideas as to what I could be doing wrong?

---

### Post by coolbrook on 2009-10-17
I'm trying to use this solution as well.

---

### Post by BadSeqtor on 2009-10-18
> **coolbrook said:**
> I'm trying to use this solution as well.
Did you have any luck?
Are you also experiencing that the top panel is staying on the laptop?

If someone reading this could give us some help it would be greatly appreciated. :)

---

### Post by BadSeqtor on 2009-10-18
I'm starting to look like Angry German Kid - surely someone here has added a resolution manually in Koala and could give us a hint?

---

### Post by 23meg on 2009-10-18
Did you try "1656x1050_60.00", including the quotes? Paste this:
```
xrandr --addmode VGA1 "1656x1050_60.00"
```

---

### Post by 23meg on 2009-10-18
By the way, the output seems to indicate the mode was actually added, despite the error. Did you try ```
xrandr --output VGA1 --mode "1656x1050_60.00"
``` to switch to the mode?

---

### Post by coolbrook on 2009-10-22
Not working on my end

```
xrandr: screen cannot be larger than 856x600 (desired size 1280x1024)

```

---

### Post by coolbrook on 2009-10-24
Now resolved by an update.  I believe this current 1280x960 is the correct resolution that I wanted.

---

