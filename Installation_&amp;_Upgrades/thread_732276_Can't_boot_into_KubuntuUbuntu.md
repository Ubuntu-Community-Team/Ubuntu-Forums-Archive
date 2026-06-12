---
title: "Can't boot into Kubuntu/Ubuntu"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by Thermonuclear on 2008-03-22
Trying to install Kubuntu right now and having trouble but I had the same problem trying to install Ubuntu awhile back.  I try booting into the OS from the safe graphics option and I get a black screen for awhile and then it boots to some KDE Manager console screen and it just stops (like loading scripts or something).  I don't know what the technical term is but it stops and lets me type in text but the sytem ignores everything I enter, as if waiting for something that never happens, here is my system,

eVGA 680i A1 motherboard
e6600 @ 3.15 ghz
eVGA 8800 Ultra w/ Zalman 
2x1gigs Mushkin Extreme Performance ram 3-4-3-2T @ 800mhz
2x500gig Samsung SpinPoint SATA II HDDs

That's all the important stuff anyways, so the disk worked in another computer I own so I know that's not the problem.  I've always had problems with Linux on my computer, I was using Mepis for awhile and I got it to work by setting it to Vesa graphics and lowered down the resolution until I was able to install the OS and proprietary graphics card drivers, after which it ran like  a champ.

---

### Post by jacksaff on 2008-03-22
You're having trouble because your graphics card is not supported by free drivers that can be distributed with the disk.
You need to select safe mode, then edit the boot line to delete the quiet and splash options.
Try that and post back if it doesn't work.
Once installed it's very easy to install the correct drivers for your card.

---

### Post by Thermonuclear on 2008-03-22
Well the good news is that I could actually read the console as it went through boot process instead of a blank screen, but my main problem seems to remain the same.  I temporarily get a blue screen that lasts about 20-30secs with a mouse cursor, and then it turns to a loading cursor and goes back to the console with the last remaining entry being "Running local boot scripts (/etc/rc.local)" and does that thing I was talking about where I can type but the system wont accept commands.

---

### Post by Thermonuclear on 2008-03-26
Nobody?

---

