---
title: "Install and boot with nosplash - why?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Chebyshev on 2007-10-19
After the 7.10 install gave me a black screen a few times, I hit F6 at the menu and changed 'splash' to 'nosplash' and got it installed. Now every time I boot I have to edit the options and change 'splash' to 'nosplash'. Why does my computer hate the splash screen?

AMD X2 3800
nVidia 8800 GTS

This is with the 64 bit iso. The 32 bit RC iso installed and ran without this problem just last week.

---

### Post by lixoman100 on 2007-10-19
I'm having the same problem with 64-bit here, on a 8800GTX conected to widescreen LCD via DVI.

Just out of curiosity (so I can at least boot into Ubuntu for now), can you explain to me how to add nosplash to Grub? I used F6 for the installation but I don't know how to do it now that it is installed.

---

### Post by Chebyshev on 2007-10-19
Select the image you want to boot in Grub, hit e then select the long line, I forget what it starts with. Hit e again and change splash to nosplash. Hit enter to save it and then b to boot.

I also have a widescreen LCD using DVI, but I can't imagine that matters. Right? Right?

Good luck!

---

### Post by lixoman100 on 2007-10-19
First of all, thank you, I'm posting this from Ubuntu now.
Second, there is a semi-permanent way of using nosplash that I just found (gonna test now): edit /etc/grub/menu.lst, search for "splash" and replace for "nosplash". It will be fixed there until something gets updating in Ubuntu that changes it back.

Now for diagnosing the problem. It only happens in 64-bit, and it seems to be related to usplash. It probably hangs the machine because, for some reason, it can't show the splash screen. Maybe because it can't set the resolution properly or can't ask the monitor about supported resolutions or something like that. So, yea, I'm kinda suspicious about the DVI connection. Unfortunately, I have no way of testing differently, since my monitor only has DVI, and so does my video card.

---

### Post by Chebyshev on 2007-10-19
I don't have an /etc/grub directory. I edited /boot/grub/menu.lst instead, maybe that will work. Thanks for the tip.

---

### Post by lixoman100 on 2007-10-19
> **Chebyshev said:**
> I don't have an /etc/grub directory. I edited /boot/grub/menu.lst instead, maybe that will work. Thanks for the tip.

Yeah, that's the one. Sorry, I mixed the directory names.


But I think that Ubuntu really can't understand my monitor. I finally got to the desktop and I can't setup my resolution correctly. Ubuntu simply can't understand that my monitor's native resolution is 1680x1050. I tried chosing generic monitors, auto-detect and even loaded configurations from my monitor's .inf, but still no dice. Hell, after 3 or 4 tries my desktop disappeared, all icons and the wallpaper. And the shutdown button doesn't even work anymore. That was after installing the restricted drivers for my GeForce 8800GTX.

Well, if you make any progress, please let me know. Until then I can't do much - can't use this monitor under 1024x768 :/


Good luck.

---

### Post by Chebyshev on 2007-10-19
I don't know what to tell you about that. The live CD booted right to 1680x1050 on my box and the restricted drivers installed fine and are working right now. Sorry to hear it isn't working out for you.

---

### Post by Falcorian on 2007-10-19
Running 64bit here, and I have the same problem on a nVidia 8800 GTS, Intel E6850, and Gigabyte GA-P35-DS3P.

---

