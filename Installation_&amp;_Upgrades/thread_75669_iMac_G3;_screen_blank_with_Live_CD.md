---
title: "iMac G3; screen blank with Live CD"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Thmanx on 2005-10-14
i ran the latest build of the PPC live CD on my G4 iMac with 0 problems. I Tried the live CD on my G3 600mhz iMac and i had problems.

I was able to see all the loading bars and chose my language, keyboard, etc.  Problems happoned when i had to chose my Resolution. It showed Resolutions up to 1920x1440 and said, "remove unsuported resoltions from list" i tried and i could not remove anything. (there was an "X" in 640x480, 800x600x , 1024x768) so i hit enter

after that screen goes black. I can hear the welcome sound, but no display.
i want to install ubuntu onto a partition on my disk but i am afraid the same no dispay problem will happen again making it useless. 

sugestions?

---

### Post by Rxke on 2005-10-14
)Moderators: move this to ppc section?)

I had this too, the first time running the installer...

you have to scroll down to the resolutions you dont want and press the spacebar to deselect them. Took me several times before I figured that out, pressing enter instead... Some installations, the install screen at this poind behaves a bit 'weird' in that the star you have to toggle on/off doesn't actually toggle, but the character on the right of it, that's ok, as long as you change the highest non-supported resolutions to 'off'  otherwise it starts up in an unsupported screenresolution....

---

### Post by ssam on 2005-10-14
if you can get to a command line by pressing ctrl+alt+f1
then run
```
sudo dpkg-reconfigure xserver-xorg
```
this let you reconfigure the graphics

---

### Post by Thmanx on 2005-10-15
i have put at '[X]' next to the resolutions my computer can handle. But After the Unbuntu logo loding screen loads, all i get is black screen still.

---

