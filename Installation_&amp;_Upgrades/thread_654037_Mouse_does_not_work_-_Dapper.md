---
title: "Mouse does not work - Dapper"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by chopsuwe on 2007-12-30
I have downloaded and burned Dapper onto a cd (Ubuntu 6.06 desktop i386)

I boot off the cd and select start/install ubuntu. 

I get as far as the desktop with the examples and install icons showing. The mouse pointer is in the middle of the screen but does not move when the mouse is moved.

I have tried several USB and a PS2 mice. In all cases the led on the bottom glows and gets brighter when the mouse is moved but the mouse pointer on screen never moves. 



The hardware is all good and works perfectly in WinXP
Mouse- logitec wheelmouse USB
- Genius Optical PS2
- cheap optical USB
- Wireless USB

Duron750
MS-6390 board with Via chipset
Onboard graphics 
512Mb ram
PS2 keyboard.

---

### Post by chopsuwe on 2008-01-02
No replies? Surely it can't be that hard to install Linux!

---

### Post by nwadams on 2008-01-02
i had the same problem with dapper
use gusty instead

---

### Post by angryfirelord on 2008-01-02
Go into your BIOS and see if there's anything USB related. If possible, select "Enable USB leacy support" and/or enable the BIOS to use the USB mouse rather than the OS.

---

### Post by chopsuwe on 2008-01-02
All legacy support is enabled. All usb ports are enabled, support for usb keyboard and mouse is eabled. All other onboard devices are enabled.

I think this is an Ubuntu issue as this pc works fine with WinXP and Ubuntu 5.1

---

### Post by angryfirelord on 2008-01-02
Yeah, I'm a bit confused as well because I have a Logitech MX518 that works perfectly fine under Dapper. Regardless, put in a Gutsy LiveCD and see if that clears up the issue or not.

& another thing, do you have a model number for your mouse or is it simply a "wheelmouse"?

---

### Post by chopsuwe on 2008-01-02
I'm on dialup and it takes literally weeks to download each version of Ubuntu. This is the third version I have tried with no success at all. I really would like some assurance that I'm not just continuing to waste my time downloading another version that doesn't work. After all I am using the long term support version!

Once upon a time there was a model number on the mouse. I have tried other mice (see first post) and they don't work either.

---

### Post by chopsuwe on 2008-01-02
Update:

I managed to install Dapper using keyboard shortcuts and in the process discovered another problem. 

If I have the keyboard (PS2) plugged in and boot off the live CD or start the instaled version the keyboard does not work. hitting Caps Lock or Num Lock does not toggle the LEDs and hitting other keys does not type anything. 

If I boot without the keyboard plugged in, then plug it in when Ubuntu is ready for an input it does work. 

Any ideas?

---

