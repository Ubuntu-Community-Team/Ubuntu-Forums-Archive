---
title: "Wont install, wont boot Live"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by cybpabeofm on 2012-03-24
My system:
FX 8120
Gigabyte 990fxa-ud3 motherboard
GTX 550 ti
usb wireless adapter
8gigabytes of PNY DDR3
PCI IDE controller (for disk drive)
1TB 7200rpm HDD

A couple of days ago I attempted an install of ubuntu from a USB HDD (I used universal USB installer to make it) and ran into a boot error. This ocurred both when I tried to boot to Ubuntu from the USB drive and when I tried to install it. I believe that the cause of this is my graphics card (gtx 550 ti) but, my motherboard has no DVI or VGA outputs so I cant remove the card. My primary operating system is windows 8 dev preview. I managed to boot live to openSUSE by adding the boot option nomodeset. I was wondering if anything like this is possible with Ubuntu?
:confused:

I have lots of previous linux experience with both openSUSE and Ubuntu, however I prefer Ubuntu.

---

### Post by cybpabeofm on 2012-03-24
This is the error I get:
5.562822] [drm] nouveau 000:01:00.0: EvoCh 0 Mthd 0x003c Data 0x00000000

Its the same thing over and over again for about 30 lines, the only area it changes are in the bolded areas:

**5.562822**] [drm] nouveau 000:01:00.0: EvoCh 0 Mthd **0x003c** Data 0x00000000


It ends with:

5.562822] [drm] nouveau 000:01:00.0: EvoCh 0 Mthd 0x003c Data 0x00000000

after that my graphics cards fans max out and I have to cut the power to the machine (holding down the power button).

---

### Post by darkod on 2012-03-24
There is a sticky on top for graphics issues including nomodeset. You should find all you need there.

---

### Post by jerrrys on 2012-03-24
This link may help you

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nomodeset&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nomodeset&sa=Search&cof=FORID:9)

---

