---
title: "Trouble with installation"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by Xeeon on 2007-07-16
All right. I use my friend's copy of the ubuntu cd, (2 different copies in fact), The first screen loads up normally, and I choose "Start or Install Ubuntu"... I wait about 5 minutes in front of a black screen. then all of a sudden a blue screen with black text and a gray background comes up with upside down L's and weird foreign characters and I can make out a little bit of the text and it says "your graphical *indecipherable* was not loaded correctly"

I've tried with Ubuntu 7.04 ISO the actual CD AND I've tried Ubuntu 6.06 ISO and the SAME THING happens each time.

here are my system specs:
Intel Celeron 1.8gHz
512 MB RAM
50GB HDD
Voodoo 3.0 video card running simultaneously with my onboard graphics card.

My friend has showed me around Ubuntu 7.04 and I want it SO BAD, it is so much better than windows, expecially when you buy crossover and any help at all will be appreciated GREATLY!

---

### Post by merlinus on 2007-07-16
Video problems.

Try Safe Video Mode, or use the text-based Alternate Desktop install cd.

-merlin

---

### Post by Xeeon on 2007-07-16
I've tried safe mode. I spose I'll try the alternate text-based installation, but if my video had problems installing it, won't I have video problems even when it's done installing and I start it up?

EDIT: I've taken my HD out of my computer and installed Ubuntu 7.04 on my HD using my friend's computer, and put the HD back in my computer and it still won't load up!

Is Linux just not for my comp?

---

### Post by merlinus on 2007-07-16
Try this:

Press "Esc" when prompted to display the grub boot menu, boot into recovery mode, login...then enter:

(or Ctrl-Alt-F1 to get to prompt)

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

or reboot...

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

Also, what video card are you using?

-merlin

---

### Post by Xeeon on 2007-07-16
all I'm using is a "Standard VGA Graphics Card" according to my computer

---

### Post by regomodo on 2007-07-16
turn off the onboard graphics in your bios settings

---

