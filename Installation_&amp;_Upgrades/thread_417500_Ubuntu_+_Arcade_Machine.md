---
title: "Ubuntu + Arcade Machine"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by davidwinter on 2007-04-21
Hi all.

I've got an old Arcade Machine box with basically the insides of a PC inside with the original arcade monitor.

It's using an ArcadeVGA graphics card, which I understand is based on an ATI Radeon chipset.

I was using Windows XP on it, just running a Sega Genesis (Megadrive) emulator. However, I would really love to use Ubuntu. I've found the dgens emulator which seems perfect. 

I booted the live CD, however it uses 800x600 resolution. I'm 100% the monitor can only handle 640x480. So currently it results in some of the screen being off-display and it can't be seen.

I tried switching to 640x480 but it all appears scrambled. I read somewhere about using the arcade monitor, that it requires being run at 15khz or something... I'm really not too sure about this. But I know for Windows, I was using the special ArcadeVGA graphics drivers. So basically, I'm wondering if there are any drivers out there I can use for Ubuntu, similar to ones available for Windows?

---

### Post by colo on 2007-04-21
If you provide us with the data sheet and/or exact specs of said display/monitor, I'm pretty sure we can tailor an xorg.cong fitting your needs very well. Special drivers are not required.

---

### Post by davidwinter on 2007-04-22
> **colo said:**
> If you provide us with the data sheet and/or exact specs of said display/monitor, I'm pretty sure we can tailor an xorg.cong fitting your needs very well. Special drivers are not required.

Thanks - I'll have a good look and get back to you. Is there anything in particular I should be looking for?

---

### Post by davidwinter on 2007-04-22
OK. This is what I managed to find on the monitor itself:

```
Screen:
    Manufacturer:   "Philips"
    - "MVA48ABK05X"
    - "EIA312"
    - "No: 0050482"
    - "Model Number: 19K7601"
    - "120V"
    - "60Hz"
    - "85W Max"
```

There's quite a few numbers, but I'm pretty sure the model number is in fact **MVA48ABK05X**

Here are the display settings I currently am using in Windows XP:

```
Monitor Settings:
    Screen Refresh Rate:    "60 Hertz"
    Color Quality:          "Medium (16 Bit)"
    Resolution:             640 x 480
```

Here are the hardware details for the graphics card that I found in the various Windows dialogs:

```
Chip Type:          RADEON 9200 PRO AGP (0x5960)
DAC Type:           Internal DAC (400MHz)
Memory Size:        128MB
Adapter String:     Ultimarc ArcadeVGA
BIOS Information:   Ultimarc V 1.1

Resource Settings:
    Memory Range:   "D0000000 - D7FFFFFF"
    I/O Range:      "C0000 - C0FF"
    Memory Range:   "E5000000 - E500FFFF"
    IRQ:            05
    I/O Range:      "03B0 - 03BB"
    I/O Range:      "03C0 - 03DF"
    Memory Range:   "000A0000 - 000BFFFF"
```

Note the 60 Hertz being used in Windows, and actually printed on the monitor... so the 15khz thing I put in my first post, I'm not sure if that's relevant for this monitor now.

Any help getting an xorg config file, would be much appreciated!

---

### Post by davidwinter on 2007-04-23
I tried using dpkg-reconfigure xserver-xorg and going through setting everything up.

I did this via ssh on my other computer.

When I then restarted, I heard the Ubuntu login screen come on (with the music) but the screen was totally blank/black.

---

### Post by colo on 2007-04-23
It would be helpful if you could attach the files /etc/X11xorg.conf and /var/lox/Xorg.0.log to this thread.

---

### Post by davidwinter on 2007-04-24
[http://davidwinter.me.uk/lab/ubuntu/xorg.conf.txt](http://davidwinter.me.uk/lab/ubuntu/xorg.conf.txt)
[http://davidwinter.me.uk/lab/ubuntu/Xorg.0.log.txt](http://davidwinter.me.uk/lab/ubuntu/Xorg.0.log.txt)

Hope they're of some help.

---

### Post by davidwinter on 2007-04-26
Would this have something to do with the horizontal and vertical scan rates? Is there anyway I can work those out? Because I don't have a monitor specification besides what I found labelled on the monitor itself.

---

### Post by davidwinter on 2007-05-05
Any further help or advice with this would be much appreciated.

---

### Post by davidwinter on 2007-05-18
Bump.

---

### Post by davidwinter on 2007-07-13
Bump.

---

### Post by Wilb on 2007-07-18
[http://easymamecab.mameworld.net/](http://easymamecab.mameworld.net/)

Loads of info for getting your arcade monitor up and running on your PC on that page.

My cab runs Dapper, radeonfb framebuffer console as well as Xorg in 15Khz so I've got access to a variety of emulators. Had problems using SVGALib though. Found all my information from googling basically, be prepared to spend plenty of time getting everything all up and running - its not a quick and easy job if you want it all running to perfection!


If you do want quick and easy, maybe you should give Lincade a try, a custom built Gentoo install for arcade cabinets... 

[http://www.pc2jamma.org/forum/](http://www.pc2jamma.org/forum/)


Wilb

---

