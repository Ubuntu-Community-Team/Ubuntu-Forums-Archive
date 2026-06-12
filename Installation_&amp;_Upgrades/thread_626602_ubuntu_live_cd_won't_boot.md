---
title: "ubuntu live cd won't boot"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by billgoldberg on 2007-11-29
I just installed ubuntu gutsy on my laptop and i'm loving it.

As i just needed to format the hdd (sata) on my destkop, i choosed to install the new ubuntu instead of reinstall vista.

I popped in the same live cd i used to install gutsy to my laptop, but i get an error when trying to boot the live cd.

So:
- I enter the disc
- I choose the first option (some thing like: run ubuntu and install)

Then the yellow bar goes left to right.

Then the bar seems to load, but after it starts error start comming

The error code is large, but i'll try to give it:

As I can't read the whole error code anymore (multiple windows), i will give the code i can still read;

" [ 384.563194] SQUASHFS error: Unable to read fragment cache block [274366b0]
" [ 384.563197] SQUASHFS error: Unable to read page, block 274366b0, size 3623

init: tty4 main process ended, respawning
init: tty5 main process (5694) terminated with status 1
init: tty5 main process ended, respawning
init: tty3 main precess (5695) terminated with status 1
init: tty3 main process ended, respawning
init: tty6 respawning too fast, stopped
init: tty5 respawning to fast, stopped
inint: tty3 respawning too fast, stpped
[ 384.566458] SQUASHFS error: sb_bread failed reading block 0x9d0e7
[ 384.566505] SQUASHFS error: Unable to read fragment cache block [274366b0]
[ 384.566598] SQUASHFS error: Unable to read page, block 274366b0, size 3623
init: tty2 main process (55697) terminated with status 1
...
you get it

I checked the disc and it said 26 error, however i just used the same disc to install gusty to my laptop.

note: new dvd player name: Optiarc DVD RW AD-7173A (label flash)

---

### Post by bigken on 2007-11-29
sounds like your hdd is damaged or badly fragmented try using the gparted liveCD to fromat the hdd 1st

---

### Post by bigken on 2007-11-29
you could also try the alternate cd

---

### Post by billgoldberg on 2007-11-29
I formatted the the hard drive using the gparted live cd. 
I formatted it to ext3.

I'll try a copy of feisty to see whether it's the cd or the hard drive.

---

### Post by bigken on 2007-11-29
why dont you try your windows cd it could be the sata not being picked up by ubuntu

---

### Post by billgoldberg on 2007-11-29
Feisty booted ok.

It seemed the culprit was some dust on the gutsy cd-rom.

I'm a bit ashamed of myself right now.

:lolflag:

Anyways, thanks for trying to help Bigken.

---

### Post by bigken on 2007-11-29
:lolflag: sack your cleaner :lolflag:

---

