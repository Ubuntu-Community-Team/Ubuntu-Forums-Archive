---
title: "LiveCD-Installation/working problem"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by sumudu on 2007-08-13
Hi Everyone.

I got new Ubantu CD last week, I have windows xp so I inserted the live cd and restart the computer, then live CD bootup and ubuntu logo screen came with booting options.

first i just choose the default..it workout and startup logo came with floating bar, then DOS type screen in which it says [ok] and then all screen go blank

second i tryied the safe booting option-result same as above but this time I got msg

   " failed to start the X server (your graphical interface). It is likely that it is not set up correctly.Would you like to view the X server output to diagnose the problem?"

and when I say yes it gives this msg


"X window sytem version 7.2.0,release date: ........,
X protocol version 11, revision 0, release 7.2
build operating system: Linux Ubuntu
Current OS system: linux ubuntu 2.6.20-15-generic #2 SMP sun
april 15 07
build date: 04 april 2007
module loader preset
markers: (--) probed, (**) from config file, (==)informational.
(ww) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) log file : "/VAR/LOG/XORG.0.LOG" time--------
(==) using config file: "/ETC/X11?XORG.config"
(ee) vesa (0): NO MATCHING MODES
(ee) SCREEN (s) FOUND, BUT NONE HAVE A USABLE CONFIGURATION.
FATAL SEVER ERROR: NO SCREEN FOUND


then I tried n it says

next screen reads : the Xserver is now disable4d. restart GDM when it is configured correctly. 


I have normal PCI VGA card from ATI , ATI RAGE XL PCI

Please help me, I want to experince ubuntu....please

Ubuntus starting screen is so cooler than win xp

---

### Post by merlinus on 2007-08-13
ATI video card problem.  Lots of folks have experienced this.

You might try this when the xserver error appears:

Ctrl-Alt-F1 to get to prompt.

```

sudo dpkg-reconfigure xserver-xorg

```You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```-merlin

---

