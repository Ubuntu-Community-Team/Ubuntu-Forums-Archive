---
title: "Screen turns off when booting"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by Diego_Rodriguez on 2014-07-22
Hi everyone,

I have just installed Lubuntu 14.04 (alternate) on an old machine (processor: 2,1 - ram: 380 or so) and I cannot boot the system properly.

After the BIOS is ready, the blue screen starts and the white dots move and as soon as it's finished the monitor turns off (no signal message).

The installation went fine but I haven't been able to log in, not even once.

When the screen is off, however, the computer is still on. Furthermore, I press CTRL+ALT+F2 to access the terminal and IT WORKS (the screen is on). There, I can log in and even use common commands. I upgraded the system (upgrade and dist-upgrade) and still I can't make it work properly. I tried to start the system by using the 'startx' command and the screen turns off again, so I guess the x server may be the problem. Unfortunately, I don't know what to do or how to fix it.

Extra info:
If (instead) I press CTRL+ALT+F1 in order to see what is going on, the last process says:
* Starting Bridge file events into upstart                        [OK]
_      <---that one blinks

Any help will be highly appreaciated. Thanks in advance.

---

### Post by LubLearner on 2014-07-28
Hi

Can it be an out-of-range resolution problem? Read this article:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

It tells how to test different resolutions dynamically:

> **Dynamically testing different resolutions**

[COLOR=#333333][FONT=Ubuntu Beta]You can either use the Screen Resolution GUI tool to experiment with different resolutions, or the more powerful xrandr command-line tool. Without parameters, xrandr shows you the names of different outputs available on your system (LVDS, VGA-0, etc.) and resolutions available on each:[/FONT][/COLOR]

[LIST]
[*]$ xrandr
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1400 x 1400
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 286mm x 214mm
   1400x1050      60.0*+   50.0  
[...]
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]You can direct xrandr to set a different resolution like this:[/FONT][/COLOR]

[LIST]
[*]$ xrandr --output LVDS --mode 1024x768
[*]$ xrandr --output VGA1 --mode 1024x768
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]The refresh rate may also be changed, either at the same time or independently:[/FONT][/COLOR]

[LIST]
[*]$ xrandr --output LVDS --mode 1024x768 --rate 75
[*]$ xrandr --output VGA1 --mode 1024x768 --rate 60
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]Note that changes you make using [/FONT][/COLOR]xrandr[COLOR=#333333][FONT=Ubuntu Beta] only last through the current session. xrandr has a lot more capabilities - see [/FONT][/COLOR]man xrandr[COLOR=#333333][FONT=Ubuntu Beta] for details.[/FONT][/COLOR]


To fix that kind of problems, the wiki article says:

> **Resetting an out-of-range resolution**

[COLOR=#333333][FONT=Ubuntu Beta]If you set a resolution inappropriate for your monitor in the Screen Resolution GUI tool, you can reset it from a terminal by running[/FONT][/COLOR]

[LIST]
[*]$ rm ~/.config/monitors.xml
[/LIST]


I do not know if this is right for your computer since you cannot log in and that folder seems an user's one. Besides, you can try the several ways it says so as to do persistent changes.

---

