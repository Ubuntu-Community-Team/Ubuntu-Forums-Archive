---
title: "Widescreen Display issue Ubuntu 12.04"
date: 2013-07-09
forum: Installation &amp; Upgrades
---

### Post by jamespatel on 2013-07-09
having used ubuntu 10.10 for a few years i upgraded to 12.04. hardware set up remains the same.
computer - Dell optiplex 755
graphics - Intel 82Q35 Express (rev 02)
VGA cable to TV PC input
TV is panasonic LCD

Ubuntu 12.04 wont recognize the widescreen 1240x720(16:9) - only options in disply settings are 1024x786 (4:3) and 800x600(4:3). have tried detect displays but no avail.
I understand this is a recurring problem with 12.04 (10.10 had no problems detecting the TV)
Have really trawled the forums/google and tried multiple solutions but no luck.
Any help would be greatly appreciated.

---

### Post by ohnonot on 2013-07-10
so ubuntu recognizes the tv but won't let you set the resolution?
you have no other screen, the tv is the one and only?
what does typing 'xrandr' in a terminal return?

---

### Post by jamespatel on 2013-07-11
many thanks for your reply
no other screens or monitors just the tv.
xrandr gives me this

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9

---

### Post by ohnonot on 2013-07-11
it truly looks like there's no straightforward way to set your tv to its highest resolution, if xrandr does not recognize it.
but i remember having read of a possibility to set a screen to "undocumented resolution".

next step would be to find your graphic card and driver:

type alt+F2, then 'hardinfo'
or, find a system benchmark analyzing monitor (not precisely, sth like that) that will tell you about your hardware - your graphic card.
then you type the manufacturer of the card in the search in synaptic (or software center, if you must - but then you might have to click "show n technical thingies" near the bottom) - to see which driver is installed.
so, if hardinfo says "Intel Mobile G965", you just search for intel. intel video, most probably.

come back here with those 2.

also, what have you tried so far and how exactly did it not work?

---

### Post by jamespatel on 2013-07-12
[COLOR=#000000]thanks for your reply
as far as i can tell the graphics card is Intel 82Q35 Express (rev 02)
i have tried adjusting xrandr to a custom or forced resolution but had no luck with that - a lot of error messages come up after restarting.[/COLOR]

---

