---
title: "Problems installing ubuntu 64 bit"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by *^kyfds( on 2012-09-08
Before i start, i'll admit that i'm not massively familar with the linux command line, and although i know a few commands, i might need some extra help when it comes to more complex commands.

moving on.

I'm having trouble installing Ubuntu 12.04 LTS 64-bit onto my self built PC, specs as follows:

Operating System
    MS Windows 7 Home Premium 64-bit SP1
CPU
    Intel Core 2 Quad Q6600 @ 2.40GHz    42 °C
    Kentsfield 65nm Technology
RAM
    4.00 GB Dual-Channel DDR2 @ 400MHz (5-5-5-18)
Motherboard
    ASUSTeK Computer INC. P5K-E (LGA775)    30 °C
Graphics
    Generic PnP Monitor (1024x768@60Hz)
    ATI Radeon HD 4800 Series (MSI)    40 °C
Hard Drives
    699GB SAMSUNG SAMSUNG HD753LJ ATA Device (SATA)    31 °C
    466GB Western Digital WDC WD5000AAKS-00YGA0 ATA Device (SATA)    38 °C
    466GB Western Digital WDC WD5000AAKS-00YGA0 ATA Device (SATA)    37 °C
    466GB Western Digital WDC WD5000AAKS-00YGA0 ATA Device (SATA)    36 °C
Optical Drives
    Optiarc DVD RW AD-5170A ATA Device
    Optiarc DVD RW AD-5170A ATA Device
Audio
    AMD High Definition Audio Device


I've tried installing Ubuntu 32 **and** 64 bit from both a live USB and a live CD,and each time the same series of events leading to an error loop appear to occur.

1. the live CD/USB boots sucessfully.

2. a series of large lines of fonts scroll past the screen.

3. the lines of text become smaller (the screen 'zooms out')

4. one single paragraph of text continuously loops, mentioning something 'failed to read EMR',   and about 6 number and letter combinations ('**&#952;&#952;X**') with theta replaced with a number or a letter

5. after about 20 seconds, the ubuntu loading screen appears, and nothing other than the loading bar itself displays any activity.

it is at this point that i have to hard restart my computer, because it gets stuck in a never ending loop


is there any fix to this problem?

(the live ISO is definitely genuine, as i get the same error with an ISO downloaded from a number of mirors, and with 32 and 64 bit).

---

### Post by afulldeck on 2012-09-08
> **Thehumorouscheese said:**
> 
I've tried installing Ubuntu 32 **and** 64 bit from both a live USB and a live CD,and each time the same series of events leading to an error loop appear to occur.

1. the live CD/USB boots sucessfully.
.

Meaning? Does that mean you get the install screen?

---

### Post by *^kyfds( on 2012-09-08
> **afulldeck said:**
> Meaning? Does that mean you get the install screen?


it got past my motherboard's bios screen, although it did not get to any install screen.

---

### Post by *^kyfds( on 2012-09-09
bump.

---

### Post by 2F4U on 2012-09-09
Have you already tried the nomodeset grub kernel parameter?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by *^kyfds( on 2012-09-12
i've identified the problem to  be with my graphics card, but i'm still not sure what to do :S

---

### Post by *^kyfds( on 2012-09-15
bump.

i'll try running ubuntu off the live CD to see if that works.

---

