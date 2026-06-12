---
title: "¨ati¨ driver not loaded and CR Tmonitor not detected in Display"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Robban59 on 2009-04-17
Hi everybody,

I just can´t get Jaunty to work correctly with my X800GTO ati video card and my Syncmaster 997MB CRT monitor; first of all although I have specified the ¨ati¨ driver in the xorg.conf it is not loaded and the VESA driver is loaded instead , how come ?  then I get the message at startup that the X-server is already running on display :0, that the specified display is busy so this server is being started on display :1, after which I get the graphical login ; then the monitor is not detected in the System -> Preferences -> Display, the resolution is ok at 1280x1024 but the refresh rate is low and not selectable. I have included the following logs : lspci log, Xorg.1.log 

Regarding the 2 xorg.conf files also included, the situation is this : using the xorg.conf.new obtained by running ¨X -configure" the X server doesn't start at all after the Ubuntu logo and the red bar , the PC freezes with blinking Scroll Lock and Caps  Lock; with the xorg.conf file, although is has an error in it ( 3 in place of an # ), I´m able to get at the end a graphic login and start Jaunty with VESA driver. 

Everything was working fine with 08.04 and Catalyst 09.02 !

Thanks in advance for any help/suggestion

---

