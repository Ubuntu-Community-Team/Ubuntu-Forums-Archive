---
title: "graphics 10.04"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by R.Schwendler on 2010-11-09
I have an old laptop (1999) running ubuntu 8.04  works ok
I also have a desktop running win xp & ubuntu 10.04 works ok
I used my live cd and installed 10.04 on the laptop
Installed ok 
When I reboot, I get display error
cannot use 1024 X 1024 not enough memory
I used the work-around. but I can't display name/password panels
I hit the keyboard and got a dos prompt.
Can I go back to the 8.04 display? I got full screen

---

### Post by tommcd on 2010-11-10
> **R.Schwendler said:**
> 
When I reboot, I get display error
cannot use 1024 X 1024 not enough memory
I used the work-around. but I can't display name/password panels

You could try being a little more specific here.
What video card is on the laptop?
What "work around" did you use? Please post *exactly* what you did as thoroughly as possible.

---

### Post by Rubi1200 on 2010-11-10
As posted above; and also we need to know how much RAM is installed.

Thanks.

---

### Post by sikander3786 on 2010-11-10
> cannot use 1024 X 1024 not enough memory

I feel lost here. Haven't heard of that resolution before, 1024 X 1024? :-( Or is it a typo?

---

### Post by chronomanta on 2010-11-23
Greetings.
 
I've got the same error. Temporarely i pass it by (simple trick), but i'm looking for hard solution. My [COLOR=black]temporary[/COLOR] solution: log in and run
startx -- -depth 16
it should work. And, what is [COLOR=black]curious, it will run X with lower (optimal) resolution (for my antique notebook - 1997 - it's 1024x768 )[/COLOR]
 
With regards.

---

### Post by chronomanta on 2010-11-23
Whole error log looks like this:
 
(II) SMI(0): Printing probed modes for output LVDS
(II) SMI(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) SMI(0): Output LVDS connected
(II) SMI(0): Using fuzzy aspect match for initial modes
(II) SMI(0): Output LVDS using initial mode [COLOR=red]1024x768
[/COLOR](II) SMI(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(EE) SMI(0): Not enough video memory for the configured screen size ([COLOR=red]1024x1024[/COLOR]) and color depth.

[COLOR=black]What's going on? Look at [/COLOR][COLOR=red]red [/COLOR][COLOR=black]signed screen sizes.[/COLOR]

---

### Post by tommcd on 2010-11-23
> **chronomanta said:**
>  
I've got the same error. Temporarely i pass it by (simple trick), but i'm looking for hard solution. My [COLOR=black]temporary[/COLOR] solution: log in and run
startx -- -depth 16

Do you have a *xorg.conf* file in your */etc/X11/* directory? If so then just change the default depth in the *Section "Screen"* section to 16.
If you do not have a xorg.conf file, then just create one and put this in it:
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    SubSection     "Display"
        Depth       16
    EndSubSection
EndSection

```
This should enable you to boot with a default depth of 16 if you want that.

---

### Post by chronomanta on 2010-11-24
> Do you have a *xorg.conf* file in your */etc/X11/* directory?
 
Of course i do. I've already commented whole 24-bit depth section, but result was the same. I will try your solution. 
 
Thanks.
 
P.S. My laptop had been worked before with 1024x768 24-bit screen.

---

### Post by tommcd on 2010-11-24
> **chronomanta said:**
> Of course i do. I've already commented whole 24-bit depth section, but result was the same. I will try your solution. 

These days, if you use the open source drivers that ship with Ubuntu, it is common not to have an xorg.con file. That is why I asked.
So just change the default depth to 16 in your xorg.conf, then reboot. You can always change it back to 24 if it does not help.
And what graphics card does the laptop have? If you do not know, post the output of:
```
lspci | grep -i vga
```

---

### Post by Mark Phelps on 2010-11-25
Ubuntu 8.04 supported ATI cards using proprietary drivers that newer Ubuntu versions do NOT support -- which is why we've asked TWICE now for you to tell us what make and model of your video card.

---

### Post by chronomanta on 2010-11-26
> So just change the default depth to 16 in your xorg.conf, then reboot.
Thank you! It works fine. I'll write my graphics card model tomorrow (i left my notebook turned off at home, so ssh will not help...). 16 bit is good depth (especially for that machine ;]), but i'll try to change it for "know how".
 
Thanks for your replies and help.
 
Best regards.
Michael.

---

### Post by chronomanta on 2010-12-01
My graphics:
 
01:00.0 VGA compatible controller: Silicon Motion, Inc. SM710 LynxEM (rev a3)

---

