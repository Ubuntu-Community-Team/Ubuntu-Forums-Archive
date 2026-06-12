---
title: "video memory ?"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by rfruth on 2005-11-09
Am in the process of picking out a video card for my soon to be Ubuntu box,  I'm from the Windows world where "integrated graphics" is to be avoided, 64 MB VRAM good, 128 or 256 MB  better - is Linux pretty much the same way (i.e. GUI interfaces require lots of video horsepower) - how about system RAM, 512 MB seems to be the sweet spot for general XP use, Ubuntu 5.10  with GNOME ?

---

### Post by ssam on 2005-11-09
yes fairly similar on linux.

Xorg (the unix graphics server) is beginning to get offscreen rendering and compositing. this means that each program draws its window to one part of the video card memory and the compositer colects all these up and draws them into another bit of video memory together and overlapping (it can also put in drop shaddows and transparency). this means you need lots of video memory, although i'd imagine 64-128mb is probably more than enough for most users.

for main ram. i would recommend 256mb as a minimum and that 512mb would make everything faster. if you wanted to use minimalist window managers and light applications then you could probably get away with 128mb.

---

### Post by rfruth on 2005-11-09
Thanks Sam one more question if you'll humor me, card reader easier than USB digital camera (Canon Powershot A60) ?  (just want to get my pics from camera to computer the easiest way) or is it 6 of one half dozen of the other :rolleyes:

---

### Post by ssam on 2005-11-10
try just plugging the camera into your computer with the usb lead. if you are lucky it will ask you if you want to import the photos. if it doesnt then it will probably be easier to get a £5 usb card reader and use that.

i use a card reader because i shoot in raw, and like to just drag the whole folder onto my hard disk, rather then import photos in to gthumb.

---

