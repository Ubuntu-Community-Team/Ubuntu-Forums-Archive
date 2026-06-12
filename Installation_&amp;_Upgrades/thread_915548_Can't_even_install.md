---
title: "Can't even install"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by popoengineman on 2008-09-10
I'm running ubuntu 8.04.1 from a disk image cd-rw and so far, the splash in Windows XP pops up and asks me what I would like to do. I want to install ubuntu onto my computer. So I click the first option, which says I must boot ubuntu from the live cd and I can install it from there.

Well I reboot my computer and it tells me everytime that ubuntu is running in low graphics mode. I try to configure the settings so it will work, but I guess I'm not picking the right things. Anyway, here are my specs (I know most of this information may not be needed but I am posting it just in case):

_Display card_

[B][SIZE="1"]Name - Radeon X800 SE
Manuf.-ATI Tech Inc
Chip - Radeon X800 SE (0x554B)
DAC  - Internal DAC (400MHz)
Total Memory - 128.0MB
Display: 1280x1024 16 bit 60Hz
Monitor: Dell E193FP[/SIZE][/B]

_Driver info_
[B][SIZE="1"]
Main Driver - ati2dvag.dll (What is the name for this driver??)
Version - 6.14.0010.6476 English
Mini VDD - ati2mtag.sys
VDD - n/a
DDI version - 9 or higher[/SIZE][/B]


When I setup, I chose the correct monitor, resolution and 60Hz, but when on the Display (Driver?) tab, I chose Radeon card, etc,
I don't even know what VESA means.

**This is what I see after a successful or unsuccessful configuration:**

[B][SIZE="1"]Starting deferred executive scheduler  [OK]
Starting periodic command scheduler   [OK]
Checking battery state... [OK]
running local boot scripts [OK]
_[/SIZE][/B]  <thats a blinking underscore

Thats all! Does nothing for hours, I've waited.

[B]
I have also tried the following:[/B]
ctrl+alt+f1/2 ... typing startx **fatal server error, caught signal 11, server aborting **

and i tried "sudo dkpg-reconfigure -phigh xserver-xorg"

If I can't even run from the CD to install ubuntu,
I'll probably just call the whole thing quits.


*edit*
Yes I am running "Live" Ubuntu from a CD, Nothings been installed, it just wont even start

---

### Post by roccity1 on 2008-09-10
Does it install to a command line at least?

---

### Post by popoengineman on 2008-09-10
> **roccity1 said:**
> Does it install to a command line at least?

If you mean the DOS style thing (I asked a friend to help me interpret what youre saying)?  Then no, it doesn't.

I dont think anything installs, Im running from the "live cd" and it wont even start. it gives me graphic card issues

Is that what you mean?

---

### Post by lisati on 2008-09-10
Are you able to boot from the CD?

---

### Post by GreatGariny on 2008-09-10
There is an alternate install disc you could try.  It uses a text based installer instead of a graphical one so it should run on anything.  Its not too different from the questions the graphical mode asks you during install.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check the box at the bottom that says: Check here if you need the alternate desktop CD.

Good luck and make sure you are double sure on partitioning if you want to keep Windows.

There is also a safe graphics mode you can enable if your CD goes to the Ubuntu menu with, install ubuntu, check memory, etc.

---

### Post by popoengineman on 2008-09-10
> **lisati said:**
> Are you able to boot from the CD?

Nope! This is where my issue lies, **I am booting the CD** and after the **Ubuntu image** and just below it, the **loading bar**, it presents me with:
[B]
Starting deferred executive scheduler [OK]
Starting periodic command scheduler [OK]
Checking battery state... [OK]
running local boot scripts [OK]
_ [/B]

the screen blinks a couple times at four second intervals, then I see an "X" cursor and a dialog box that says my graphics card couldnt be identified and that ubuntu is running in low graphics mode. It gives me the option of configuration, but either way, i still always end back at this screen:

[B]Starting deferred executive scheduler [OK]
Starting periodic command scheduler [OK]
Checking battery state... [OK]
running local boot scripts [OK]
_[/B]

---

### Post by popoengineman on 2008-09-10
> **GreatGariny said:**
> There is an alternate install disc you could try.  It uses a text based installer instead of a graphical one so it should run on anything.  Its not too different from the questions the graphical mode asks you during install.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check the box at the bottom that says: Check here if you need the alternate desktop CD.

Good luck and make sure you are double sure on partitioning if you want to keep Windows.

There is also a safe graphics mode you can enable if your CD goes to the Ubuntu menu with, install ubuntu, check memory, etc.

Thanks. In the meantime while trying to troubleshoot my problem, I will look for the alternate disk download for DVD-RW iso, that is all I have (DVD-RW, not CD-RW) right now.

---

### Post by roccity1 on 2008-09-11
If you press ctl+alt and f1 or f2 does it drop you to a terminal?If it does you could try using the vesa driver which is generic but it should work to get you graphical though.

IF it does type nano /etc/X11/xorg.conf

look for a line that says Section "Device" and driver change the driver to vesa and save with ctl x then press y to save.

---

