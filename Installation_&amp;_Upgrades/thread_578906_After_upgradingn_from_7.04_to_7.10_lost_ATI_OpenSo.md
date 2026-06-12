---
title: "After upgradingn from 7.04 to 7.10 lost ATI OpenSource 3D acceleration"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by xtracto on 2007-10-17
Hello, I would really appreciate your help:

Just some days ago I upgraded my Ubuntu distribution from 7.04 to 7.10 (using the sudo upate-manager -d command) and *almost* everything went smooth... except for the 3D video acceleration  (yay, the linux 3D hell ).

The way I had 3D working in the Ubuntu 7.04 was using the open source ati drivers (Driver "ati")  and it worked *wonderfully* with direct rendering, but after upgrading I saw that I had no more 3D acceleration, the results of glxinfo is:

```

name of display: :2.0
display: :2  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:

```

I have followed the tutorial at [https://help.ubuntu.com/community/RadeonDriver#head-0476c5f6d1013b85b4e1fa65205b00e3f9262d3c]The ATI Radeon open-source driver HowTo]("https://help.ubuntu.com/community/RadeonDriver#head-0476c5f6d1013b85b4e1fa65205b00e3f9262d3c") but I still get no direct rendering.

Another clue I got was after looking at the x.org log file, I get the following: 

```
(EE) AIGLX: Screen 0 is not DRI capable
```

But my card *is* capable and is supported by the open source drivers (ATI RS300M or  Radeon 9100 IGP).

Please someone help me! where else can I look for possible solutions?

thank you.

---

### Post by Pumalite on 2007-10-17
Have you looked at ENVY? I think they found a workaround for Gutsy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by xtracto on 2007-10-18
Hi, and thanks for your answer but the problem is that I can NOT use the restricted drivers as there is no 3D support for my chipset in those. Therefore the only option I have is to use the open source drivers...


They were working very well with 7.04 !! I can not make them work on 7.10... yesterday I stayed awake until about 4:00am trying to figure out what happened... it seems that everything is working (I get the radeon and the agp_art modules loaded in the kernel) and also the windows and background are rendered in a different way than normal. The desktop background for example instead of being drawn from top to bottom is drawn like in two triangles (I can perceive the two triangles as they are rendered). 

However, I run glxinfo and I do not get direct rendering... of course when I run glxgears it is very very slow.


Can someone help me?? I really do not want to re-install the Operating System as I have configured it to my taste and I have installed some applications... it will be unacceptable to start from scratch every time you need to upgrade...

---

