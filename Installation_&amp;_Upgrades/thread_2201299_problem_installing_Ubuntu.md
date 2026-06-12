---
title: "problem installing Ubuntu"
date: 2014-01-23
forum: Installation &amp; Upgrades
---

### Post by manderman85 on 2014-01-23
So I have been trying to install ubuntu 64 bit on a separate partition but my laptop keeps shutting down in the middle of the process then it makes me wait 20-40 sec before it will allow to to try and turn it back on. I thought it might be a heating problem but i can open my windows with out a problem also it says the avg temp for the cpu is around 70-80 C which should be normal. My computer had a problem with heating around 4-5 months ago but i got a fan and it seems to be helping out, it stopped shutting off. It did manage to run from the disc for a little bit but then the same thing it just totally shuts off with no warning, I mean nothing happens it just goes dark then the lights go off a few secs later. Perhaps I need the 32-bit version?

according to some of the testing done it should work just fine on my laptop 
Laptop info

Operating System
    MS Windows XP Professional 32-bit SP3
CPU
    Intel Mobile Core 2 Duo T7400  @ 2.16GHz    66 °C
    Merom 65nm Technology
RAM
    2.00 GB Single-Channel DDR2 @ 332MHz (5-5-5-15)
Motherboard
    Hewlett-Packard 309F (U10)    68 °C
Graphics
    Default Monitor (1600x1200@60Hz)
    512MB Quadro FX 1500M (HP)    83 °C
Hard Drives
    98GB Hitachi HTS721010G9SA00 (SATA)    36 °C
Optical Drives
    HL-DT-ST DVDRAM GSA-T10N
    PEX LAR09AVK SCSI CdRom Device
Audio
    SoundMAX Integrated Digital HD Audio

---

### Post by Bashing-om on 2014-01-23
manderman85; Hi !

ubuntu should load and run fine on that box.
Have you "tested" ubunu ?
Cold boot the installDVD, and as soon as the bios screen clears, depress and hold the left shift key -> 
language screen -> escape key to accept the defaults -> Boot options screen.
Select "try ubuntu".

It will take a l o n g time to load up .. a lot going on to load and run ubuntu totally from from ram/DVD -
Now do you boot to the desk top ?

Depending that outcome is what direction we take off in.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mastablasta on 2014-01-24
your temperatures are a bit high. if oyu need to wait before oyu can turn the ocmputer back on it means it is still a heat issue. 

note that Ubuntu (unlike old windows) uses 3D hardware acceleration to run the desktop alone. you might get a better outcome with Lubuntu or Xubuntu (these do not have 3D accelerated desktop). you need to solve overheating issue. if all fans are working as they should and all air vents are clean then you might be able to modify the fan speed later on (if necessary).

furthermore you might need nvidia proprietary GPU drivers. opensource should work, but who knows they might be doing something on your GPU to overheat it.

finnally, 64bit image is OK. this is not the issue here.

---

