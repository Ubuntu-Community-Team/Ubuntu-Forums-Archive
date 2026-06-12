---
title: "Screen resolution issue"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by jrodimusprime on 2010-02-10
Attempting to load without install. Cannot see the gui. Can see console.

With graphic safe mode on screen flickers, can only see console.

Tried various different vga modes(vga=771 etc), have tried modes that work for my monitor as tested in XP (1024x768x32 etc). Can see them briefly when I ^F7 it, then screen says unsupported.

Tried:
 sudo dpkg-reconfigure xserver-xorgbut it just gives me a newline, I'm guessing because it's just running in CD mode.

Can't run it in full install mode because I have a hdd issue (that I am trying to fix with the install disk).

Monitor refresh rate is 60 but I don't know if you can specify this in the boot args. I don't own any other monitors, it's a samsung lcd tv. Painful issue.

Any other args I should try? Anyone had a similar issue?

---

### Post by khelben1979 on 2010-02-11
What version of Ubuntu are you trying to install? 

Also, post an output on your graphics hardware by typing:
```
lspci | grep VGA
```

---

### Post by jrodimusprime on 2010-02-12
Ubuntu 9.10 is the ver. Is it worth attempting to install an older ver?

lspci | grep VGA:  00:0d.0 VGA compatible controller: nVidia... 6150SE.

Monitor is a Samsung la32r81bdx. 

xrandr 'Can't open display', might be because it's not installed.

---

### Post by jrodimusprime on 2010-02-12
tried with:

noapm debian-installer/framebuffer=false. X screen appeared for 1 second and disappeared as usual, but terminal windows were not visible.

xforcevesa - just make screen blink intermittently in console, couldn't see X.

beginning to think it's the LCD tv's fault - and of course it lacks any decent config.

---

### Post by khelben1979 on 2010-02-12
If you use the nonfree nVidia driver you should have no serious issues with a flicker free screen over there.

Can you check what driver version you got installed?

---

### Post by jrodimusprime on 2010-02-12
interestingly when i attempted to run 8.04 with vga=ask it says there are no VESA modes available, only the vga 80x60 etc modes, none of the 800x600x16 etc modes.

HOWEVER

running 8.04 in safe graphics mode worked. that will have to do for the moment eh.

---

