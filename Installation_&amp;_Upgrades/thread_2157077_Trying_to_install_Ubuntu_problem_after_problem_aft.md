---
title: "Trying to install Ubuntu problem after problem after problem"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by joeytwomugs on 2013-06-24
I have a macbook pro and have tried to install ubuntu via cd which just seems to do nothing as cd drive not spinning when I restart holding c down. So I am now trying to install from a usb thumb drive, how do I make an ubuntu USB bootable thumb drive from a mac? I have the ISO but the instructions I seem to find all seem to say something like... 
[LEFT][COLOR=#333333][FONT=Ubuntu]

Convert the .iso file to .img using the convert option of hdiutil (e.g.,hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]**Note:** OS X tends to put the .dmg ending on the output file automatically. 


What does that mean? I don't think I have hdiutil, can someone give me some exact steps to take. I suspect that this is going to require terminal commands which I am not hugely familiar with. Please bear in mind I am just a normal computer user and while I can open terminal etc I do not automatically know what I should be typing into it.[/FONT][/COLOR][/LEFT]

---

### Post by Treekodar on 2013-06-24
Try this: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Haven't tried it on a MAC, but it's really simple to do on a PC at least.

---

### Post by joeytwomugs on 2013-06-24
Thany you so much for replying, it sounds good, I had already downloaded UNetbootin but was thrown by two pieces of information it asks you to enter which are...

Space used to preserve files across reboots (Ubuntu only):

and...

Drive: (which offers /dev/disk0s4 or disk0s5 or disk0s6)

I have no idea what to enter in those two options.

---

### Post by joeytwomugs on 2013-06-24
Okay I've managed to get it to install the boot software onto one of my mac's partitions and moved it from there onto a USB stick. When I boot from the USB stick I get a black screen with the single letter [COLOR=#333333][FONT=arial]Ù (with the little line over it) in red lettering with a red background immediately surrounding the letter. Nothing else happens, this is pretty much the same as when I tried to boot from CD.

I mentally prepared myself for the search I would need to do to find the drivers for my mac but not even being able to install the OS is demoralising.[/FONT][/COLOR]

---

