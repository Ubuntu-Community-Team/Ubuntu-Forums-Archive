---
title: "Blank screen after X loads with ati driver"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by bartman on 2007-05-14
Hi!

I've just reinstalled Feisty on my notebook because the update from edgy broke my install. :(
I have an FirGL V5000 (some Radeon X700) graphics card and _I have tried using different drivers_ in xorg.conf:
[LIST]
[*]"**ati**": when X.Org starts there is no image on my screen. I can hear the drum telling me to log in and when I eneter my username and pass I can hear the GDM login sound as well. But the display is completely blank.
[*]"**radeon**": driver not found
[*]"**vesa**": no compatible screen found
[*]"**vga**": *works* with 320x240 8-bit depth!  Not very usable.
[*]"**fglrx**": Doesn't really work. I get the same blank screen as with ati driver BUT: when I press the LCD lid down button and release it the mouse cursor appears and the background alternates between black and some funky grey characters (_see attachments_). Also, when I run _fglrxinfo_ I get this output:```

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0
```
[/LIST]

If anyone has any ideas how to get a proper display back please post. Thank you!

---

### Post by bartman on 2007-05-16
With all the fussing around the xorg.conf I seem to have deleted it at one point. I think it happened after the fglrx installation.

After examining the logs I found out that the _X server didn't find a config_ file and used some default configuration instead, the result of which the kind of image the upper two screenshots show.

After copying the config file in place I get a proper image! But sadly no direct rendering yet.

---

### Post by stchman on 2007-05-16
> **bartman said:**
> Hi!

I've just reinstalled Feisty on my notebook because the update from edgy broke my install. :(
I have an FirGL V5000 (some Radeon X700) graphics card and _I have tried using different drivers_ in xorg.conf:
[LIST]
[*]"**ati**": when X.Org starts there is no image on my screen. I can hear the drum telling me to log in and when I eneter my username and pass I can hear the GDM login sound as well. But the display is completely blank.
[*]"**radeon**": driver not found
[*]"**vesa**": no compatible screen found
[*]"**vga**": *works* with 320x240 8-bit depth!  Not very usable.
[*]"**fglrx**": Doesn't really work. I get the same blank screen as with ati driver BUT: when I press the LCD lid down button and release it the mouse cursor appears and the background alternates between black and some funky grey characters (_see attachments_). Also, when I run _fglrxinfo_ I get this output:```

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0
```
[/LIST]

If anyone has any ideas how to get a proper display back please post. Thank you!

Feisty uses an ATI restricted driver that is just a click away.  It worked with my Radeon Xpress 200M.  It is in the Administration--->Restricted Drivers I believe.

---

### Post by bartman on 2007-06-16
I had problems loading X so there was no graphical interface. I couldn't acdcess those menus.

Weel, in the 4 weeks since the install the problem came back, i don't know why exactly...

I found a [support site in the wiki for my laptop model](https://wiki.ubuntu.com/LaptopTestingTeam/HPNW8240) with a bunch of links to bugzilla about this behaviour. I'll be trying those solutions next...

---

