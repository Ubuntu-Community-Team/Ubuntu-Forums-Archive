---
title: "jaunty and intel 4500"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by thor2002ro on 2009-03-07
i just bought a new laptop for myself and i cant seem to get the intel 4500 mhd to work with wine games .... openarena works linke a charm bun when trying to get eve online to start in wine the screen goes black and hole desktop freezes , i enabled the ctrl-alt-backspace x restart and even that doesent work  so its compleate freeze not just X 

i tried using drivers from [http://ppa.launchpad.net/xorg-edgers/ubuntu](http://ppa.launchpad.net/xorg-edgers/ubuntu)
still no change 

if i try intrepid it doesnt freeze anymore get into the game but all i se are flashes(compiz/no compiz the same) and the graphics are extreamly slow

if i try cedega tests it shows no opengl and no 3d 

anyone knows of this problem?

---

### Post by Tich666 on 2009-03-07
I'm afraid to say it, but for gaming you've chosen a suboptimal combination of video card and operating system.

I haven't tried running games in wine other than Warcraft 3 (runs fine) on my 4500mhd as I usually boot into vista for gaming.
I'm also using the xorg edgers driver and the 2.6.29rc7 kernel which can be found here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I've also enabled UXA as performance seems better with the trade-off of having to deal with infrequent lockups (only occured to me when using compiz and with the 2.6.1 intel driver, which is now out of date).

You can find more info about UXA here:
[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

Good luck with your testing and make sure to report any results back, I'm glad for every tip I get to make my laptop perform better and more stable.

---

### Post by thor2002ro on 2009-03-07
not even war 3 works ... i hear the movie... no video just blank and then it exits

i had uxa enabled allready

---

