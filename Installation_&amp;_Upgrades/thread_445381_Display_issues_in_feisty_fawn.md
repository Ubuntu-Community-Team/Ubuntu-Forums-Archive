---
title: "Display issues in feisty fawn"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by vi9er on 2007-05-15
Hi all,
I have installed feisty on my computer, and i am having a few display issues.  I have a Radeon 9250 graphics card, with VGA and DVI out.  I use the DVI connected to a TV, and don't use the VGA, unless i am trouble shooting.

The first issue i have is that DVI will not display until ubuntu has reached the login screen.( i had the exact same issue with windows) ONce it reaches the login screen, it displays, then leads into problem 2...

Problem 2 is that the desktop displays too large for the DVI display. When i connect a monitor to the VGA output, it displays correctly, but the DVI displays larger the the actual screen size.

I appreciate any help that you can give me!

THanks,
Ed

---

### Post by veloce on 2007-05-16
> **vi9er said:**
> Hi all,
I have installed feisty on my computer, and i am having a few display issues.  I have a Radeon 9250 graphics card, with VGA and DVI out.  I use the DVI connected to a TV, and don't use the VGA, unless i am trouble shooting.

The first issue i have is that DVI will not display until ubuntu has reached the login screen.( i had the exact same issue with windows) ONce it reaches the login screen, it displays, then leads into problem 2...

Problem 2 is that the desktop displays too large for the DVI display. When i connect a monitor to the VGA output, it displays correctly, but the DVI displays larger the the actual screen size.

I appreciate any help that you can give me!

THanks,
Ed

I thought Feisty had sorted those issues out - has for me.

To get the resolution on the DVI display correct, try using the "virtual" option in xorg.conf.  It's normally to allow a virtual screen bigger than the actual screen can display, but can be used to limit the virtual size to the actual size.  Might be worth a try anyway.

---

### Post by Doomguy0505 on 2007-05-16
Also check if there are any proprietary drivers that you might need to enable (System -> Administration -> Restricted Drivers Manager)

---

### Post by vi9er on 2007-06-08
Can't seem to find what i am looking for in the forums.  Any chance someone could tell me how to insert the virtual so the screen is smaler?

---

### Post by veloce on 2007-06-09
> **vi9er said:**
> Can't seem to find what i am looking for in the forums.  Any chance someone could tell me how to insert the virtual so the screen is smaler?

```
Section "Screen"
       Identifier "Viewsonic VE710b Screen"
       Device "D520 945GM 1"
       Monitor "Dell E196FP"
       DefaultDepth 24
       SubSection "Display"
               Depth 24
               Modes "1280x1024" "1024x768"
               # This next line has been found useful when xinerama automatically makes 
               # the two screens the same virtual size - this command can be used on the 
               # lower resolution screen to limit it to the resolution it can display 
               # without scrolling.
               virtual 1280 1024
               viewport 0 0
       EndSubSection
```

Here's the relevant section from my xorg.conf.  In each display subsection of the screen section add the virtual line.  Set it for the resolution you want your TV to display.

---

