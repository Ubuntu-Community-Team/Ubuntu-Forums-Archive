---
title: "Can't install ubuntu"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by haze730 on 2012-09-14
No matter what I do, my PC either gets stuck at a blinking cursor, or it reboots itself while trying to get ubuntu 12.04.1 to install (64-bit).   

I get to the man and keyboard screen.  I've tried nomodeset, no acpi etc.  I've tried alternate disc, usb, and DVD.  I've checked the md5 hashes on all iso's.  I've unplugged unnecessary devices.  I've taken out my graphics card and used onboard, i've taken out my sound card.  I've tried 10.04.4 to see if I could just upgrade and got the same result as the 12.04 discs.  I've set bios to fail-safe defaults.  Live CD does the same thing. 

The farthest I get is text on the screen (if i delete quiet and splash)  it does something like this(from my memory, not exact):
cpu #1
not responding
cpu #2
not responding
cpu #3

Then it flashes a bunch of text and reboots my machine. 

_Edit:_ it also reboots if I try to check the cd for defects.
 
I currently have Win7 64 bit installed, I took a 200gb partition out of my 1tb drive to try to install ubuntu on, but I can't get passed the first screen.

**_System specs:_**
_CPU: _               AMD Phenom II 965 BE
_Motherboard:_  GA-MA785G-UD3H
_Ram:_               4GB G.Skill DDR2 1066
_Video: _            AMD Radeon HD 6870  (HD4200 Onboard usually disabled)
_Sound:_            Creative Sound Blaster X-Fi Xtreme Gamer


I'm pulling my hair out.  Some help would be much appreciated, thanks!

---

### Post by tienlbhoc on 2012-09-14
try ubuntu 32 bit :)

---

### Post by 2F4U on 2012-09-14
Here is a discussion of people having very similiar problems than yours:

[http://ubuntuforums.org/showthread.php?t=1289119](http://ubuntuforums.org/showthread.php?t=1289119)

Most of the time it comes down to either a single USB device that causes problems, or a faulty usb hub. In most of the cases, removing the offending device solves the problem, but of course you first need to find it.

---

### Post by haze730 on 2012-09-14
Awesome!!! Thanks.  It was my dirty rotten Microsoft keyboard.  It's been acting funny the last few days too. Hmmm.  Solved.

---

