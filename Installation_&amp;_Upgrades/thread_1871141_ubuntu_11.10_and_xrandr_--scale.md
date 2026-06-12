---
title: "ubuntu 11.10 and xrandr --scale"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by josvanr on 2011-10-28
Hi 

on my small laptop screen I use

xrandr --output LVDS1 --scale 1.5x1.5

to be able to fit more on the screen. This used to work
in ubuntu, but now I tried the 11.10 live cd and
it doesn't seem to work anymore. The desktop scales
down to a small portion of the screen, the rest
of the screen turns black. IE the desktop doesn't scale
up with the screen. How can I do this (if possible)?

josvanr

---

### Post by MAFoElffen on 2011-10-28
> **josvanr said:**
> Hi 

on my small laptop screen I use

xrandr --output LVDS1 --scale 1.5x1.5

to be able to fit more on the screen. This used to work
in ubuntu, but now I tried the 11.10 live cd and
it doesn't seem to work anymore. The desktop scales
down to a small portion of the screen, the rest
of the screen turns black. IE the desktop doesn't scale
up with the screen. How can I do this (if possible)?

josvanr
Here is what the current manpage for xranr in 11.10 says: 
>  
--scale xxy
      Changes the dimensions of the output picture. [COLOR=Red]Values superior to 
      1 will lead to a compressed screen (screen dimension bigger than
      the dimension of the output mode),[/COLOR] [COLOR=Teal]and values below 1 leads to a
      zoom in on the output.[/COLOR] This option is actually a  shortcut  ver&#8208;
      sion of the --transform option.
It is stll the same as it was for previous versions.  9As far as I can tell.)

But what you are trying and what it is doing "is" how it's supposed to work...

You are telling it to compress the horizontal and vertical DPI.  It is compressing it to less than whole and therefore now has a black border around it... 

As my past experience tells me from doing this with xrandr and xorg.conf- 

Usually when I am using the xrandr scale function I use a compress (>1) or enlarge (<1) value with one half of the parameter, with the other half of the parameter as equal to 1, to fit a screen dimension.  (HDMI, Widescreen, projectors, etc.). If you use less than 1 value on both sides of the parameter it enlarges the whole screen with some of the screen usually spilling off the display.  Then you have to add a pan parameter to be able to pan to the extended part of the screen.

This is basically the same in xorg.conf with pan and dpi options.

Did I explain that well enough, or do a need to get more basic? (Don't know the target audience skillset yet...)

EDIT- You could combine that all with a mode or modeline to create a resolution to add more to a screen then scale it to your display... Sort of like multiple displays actually resolution is display1 res plus display2 res, split between 2 screens.... then scale down to fit the display.  Your card would have to support that resolution...  

What video chipset?

---

### Post by josvanr on 2011-10-28
hello,

in my previous installation it used to work: the command just scaled up the screen, the mode stays the same. Using --scale 2x2 you can eg squeeze a double size screen into the mode. The gnome desktop used to scale accordingly (ie not turn black half way). 

The kde desktop still displays right, ie I don't see a small screen in a black area. Using --scale 2x2 just makes the desktop twice as large. (without changing the mode, we stay in the same mode for the graphic card). Also, windows display correcly on this enlarged screen. (ie also on the extra area). Only the mouse now cannot move outside the original area ie stays in the rectangle of size equal to that of the mode...

Not shure about my chipset....

josvanr

---

### Post by MAFoElffen on 2011-10-28
> **josvanr said:**
> in my previous installation it used to work: the command just scaled up the screen, the mode stays the same. Using --scale 2x2 you can eg squeeze a double size screen into the mode. The gnome desktop used to scale accordingly (ie not turn black half way). 

The kde desktop still displays right, ie I don't see a small screen in a black area. Using --scale 2x2 just makes the desktop twice as large. (without changing the mode, we stay in the same mode for the graphic card). Also, windows display correcly on this enlarged screen. (ie also on the extra area). Only the mouse now cannot move outside the original area ie stays in the rectangle of size equal to that of the mode...

Not shure about my chipset....

josvanr
```

lspci -vnn | grep VGA

```

---

### Post by josvanr on 2011-10-29
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02) (prog-if 00 [VGA controller])

hi MAFoElffen,

here's the output. I already filed a bug report. Some time ago (a year) there was a similar issue, which was resolved then. I guess they'll do that this time aswell. (Unless you are right and the behaviour is as it should be..)

josvanr

---

