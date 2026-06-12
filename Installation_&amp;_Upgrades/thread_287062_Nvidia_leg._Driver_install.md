---
title: "Nvidia leg. Driver install"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by brad1138 on 2006-10-28
Trying to install driver for Geforce 2 card I have. Nvidia site says DL file then Type "sh NVIDIA-Linux-x86-1.0-7184-pkg1.run" to install the driver. When I hit alt-F2, type that and click "run" nothing happens, no program runs, the F2 dialog box just closes, nothing seems to happen. The video card is capable of 1600x1200 but it is only giving me options for up to 1024x768. What am I missing?

Thanks,
Brad

---

### Post by jem7v on 2006-10-28
I'm having Edgy/Geforce2 issues too.

Guesses about this:
1. You might want to try running that in a terminal instead of a Run dialogue so you can see if there's any feedback there. Some things sorta only run properly in a terminal.
2. If you're still using the generic driver (nv instead of nvidia, set in your /etc/X11/xorg.conf file) you Might be restricted to lower resolutions?
3. Alternately, this might be a stupid question because I'm sure you've thought of it before, but can your monitor handle anything about 1024x768? Mine can't because it's an old 15".

This thread might help with the resolution issue, but then again, maybe not:
[http://www.ubuntuforums.org/showthread.php?t=286648&highlight=resolution](http://www.ubuntuforums.org/showthread.php?t=286648&highlight=resolution)

---

### Post by jem7v on 2006-10-29
Okay, I definitely figured out how to use those drivers. Follow my instructions here if you dare!
[http://www.ubuntuforums.org/showpost.php?p=1680904&postcount=84](http://www.ubuntuforums.org/showpost.php?p=1680904&postcount=84)

---

### Post by hikaricore on 2006-10-29
For your resolution in X, you need to open a terminal and run:

```
sudo dpkg-reconfigure xserver-xorg
```

This will walk you through setting up your video hardware config file for X, once you get to the end there will be an option for you to choose between Medium, Advanced, and an option I forget because I never use it.  Choose medium and select a video mode that you know to work for your card & monitor and then choose either 16 or 24 bit (when in doubt choose 16 as 24 bit behaves oddly with some hardware in X).  Then crtl+alt+backspace after it saves the config and exits.  This should increase your resolution.  :)  As far as the drivers I think jem has that covered pretty well.

---

### Post by brad1138 on 2006-10-29
Thanks for help, I started another post as a rant and it has turned into help as well, it has 22 posts at this moment and can be found here [ http://www.ubuntuforums.org/showthread.php?t=288277 ]( http://www.ubuntuforums.org/showthread.php?t=288277 )
I just want to merge the two.

hikaricore, I tried what you said and got into a lot of questions I didn't have the answer to or understand. so I exited out half way through, hope it didn't screw things up.

Thanks again,
Brad

---

### Post by hikaricore on 2006-10-31
It won't screw anything up exiting it early it saves twice in the processes and tells you before each save.  sorry I should have pointed you to a better reference than my vague details >.<

---

