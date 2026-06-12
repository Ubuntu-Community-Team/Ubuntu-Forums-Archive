---
title: "screen resolution problem help!!"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by adamgram on 2008-11-22
I just put Ubuntu 8.04 on my Dell Dimension E521 using and old saved-from-the-trash-at-work Gateway 2000 Vivtron 21 Monitor.  [http://www.cis.upenn.edu/~kellyann/desktop/monitorspecs.html](http://www.cis.upenn.edu/~kellyann/desktop/monitorspecs.html)

The monitor has 3 possible resolutions, and the only one automatically detected is 800x600, which has everything looking HUGE and I not fitting near enough on the screen.  I go to system-->preferences-->screen resolution and 800x600 is the highest possible resolution.  The refresh rate was set to 60Hz, with the only other option, 57Hz, not making a difference.  According to the specs linked above I need for this to be at 75Hz to get a readable screen resolution.  

I've spent hours trying everything I could find on here and elsewhere on the net... I can't figure it out and it's driving me completely insane!!!  PLEASE someone help me!!!

I played with the screen and graphics preferences by typing 
gksu displayconfig-gtk
in the terminal.  It's set to 'Plug 'n' Play'.  Changing from that brings a list of monitors, including the vivtron series up to 20, but NOT 21!!!!  Are the Ubuntu repositories just missing a driver for this old-*** monitor?!?!  

Next I tried some crazy **** following this how-to
[http://ubuntuforums.org/showthread.php?t=83973&highlight=screen+resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=screen+resolution)
It screwed a lot of stuff up before eventually bringing it back to where I started.  I really don't understand what I was doing through that how-to.

Anyway, SOMEONE PLEASE HELP!!!!  It's unusable the way it is, and old and heavy as it is, the monitor is nice and big, and I want to be able to use it!  Thanks in advance!!!

---

### Post by adamgram on 2008-11-22
OMFG!!!

It isn't that hard... system-->administration-->Hardware Drivers

enable proprietry drivers

---

