---
title: "Ubuntu is being wierd..."
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by stereofreak69 on 2007-09-18
Hey, i need the expertise of the members.

I have a PC that was broken. It was Win2000 (Or the HDD i used MAY have been Win98, im not sure). When it boot up, in normal and safe mode, i would get the blue screen of death. So i ordered Ubuntu CD's over the internet, and finally got it. Then i put it in, and ran the live cd. It ran slow, but good. No errors, and internet works. So i decided to install it. I followed the install guide, and about 30 minutes later, it said install complete. So i clicked restart, when it turned off, i took the cd out. Then it checked all the stuff, and said something like:

CD Drive:
CD Drive:
PLEASE INSERT SYSTEM BOOT DISK AND PRES ANY KEY TO RESTART

SO i got mad, and threw in a old win98 restore CD. It went through the scans, then it was about to install, and said system is not compatible. So i resarted and it said the same thing.

What do i do? I need some form of OS on it, linux or whatever. My PC can burn CD's (Modern tech, ha?), so if someone knows where to get an image of windows or something...?

Someone please help!

Stereofreak69

---

### Post by arkara on 2007-09-18
i think this is a bios problem
the bios tells your computer to boot from the cd-rom and not from the hard drive
try to reinstall ubuntu and during startup press F12 or DEL to enter bios setup. and go to the boot device and then choose the order of the devices first cd and then hard drive
the live cd is slow. the installed system is much faster..
i hope i helped

---

### Post by stereofreak69 on 2007-09-18
Ok, i will reinstall it now, and press F12 or DEL during startup!

This is my first Linux OS. This is my first non-windows or apple OS for that matter...

Stereofreak69

P.S. Anything else to try if that dont work?

---

### Post by stereofreak69 on 2007-09-18
In bios, i have this set under Advanced BIOS Settings:

Virus warning: disabled
CPU l2 cache ecc checking: enabled
Quick power on self test: enabled
First boot device: HDD-1
Second boot device: HDD-0
Third boot device: LS120
Boot other device: Enabled
Boot up floppy disk: disabled
Bootup numlock status: On
Typematic rate setings: Enabled
Typematic Rate (Chars/Sec): 30
Typematic Delay (Msec): 250
Security Option: Setup
MPS Version control for OS: Enabled
Display Small Logo: Disabled

Should i hit F7 to "Optomized Settings"? And i only have 1 HHD, so i dont know why theres 3 options...

Stereofreak69

I tried reinstalling it, it didnt help.

---

### Post by PmDematagoda on 2007-09-18
Could you post the specs of your computer?

---

### Post by stereofreak69 on 2007-09-19
Like i told you, i think, im fixing it for a friend. The only time i auctually had it booted was when i was running off the ubuntu live CD. Seems to work there...

Stereofreak69

It says mainboard when it boots up...

---

### Post by PmDematagoda on 2007-09-21
Try switching HDD-1 with HDD-0 on boot devices.

By the way what is LS120?

---

### Post by Gremlinzzz on 2007-09-21
Get any system you want 
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by maybeway36 on 2007-09-21
You could try to see if you can even boot FreeDOS from the HDD, for testing purposes. The tiny fdbasecd is available at freedos.org.

---

