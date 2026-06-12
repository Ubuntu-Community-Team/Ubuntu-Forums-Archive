---
title: "Blank Screen on Install..."
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by charles.g.moore on 2006-06-24
Let me begin by saying I know nothing about linux, I played around in a buddys' system and thought it might be cool to learn something new

I just Downloaded the desktop i386 version ~700Mb Kubunto 6.x.x 
Burned the ISO onto a 700Mb CD and stuck it into my PC

AMD 2.0
MOBO Abit NF-7S
1G Ram
HDD 80Gig (Empty)
Radeon 9600 Pro (or something like that, I know the #'s are right)

So anyway, I start up the system and get the main Kubunto screen
start/install kubunto
start in easy graphical mode 
etc.
etc.

I start kubunto and the system begins to give me what it's loading and all of the lines end with an OK

The system kicks to a blank screen with a cursor in the top left corner, the cursor blinks about 6 times and then disappears. The screen is blank and I hear the CD-ROM slowly spin down and it doesnt start up again.

I ran half of the memory test and it came back with:
test Bad Err Bits Count
5 ffffffff 00000100 1

#of errors 595

I also tried starting the system in the easy graphics mode, same thing.
I changed the VGA res. to 600X800 32, same thing.

I'm not sure its a graphical thing anyways.

Any help would be greatly appreciated, I know that I probably did not give the right info as far as you need but im not really sure what info you guys would need.

---

### Post by cacharreo on 2006-06-24
I think you have selected default  monitor resolution tha is not supported by this one.
Start in terminal mode and try:
***sudo dpkg-reconfigure xserver-xorg***
Be sure that the resolutions and frequencies that you select on the monitor configuration are supported by your monitor

---

