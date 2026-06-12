---
title: "[SOLVED] Can't install on Asus P5K"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by conphara on 2007-11-09
Can somebody help me installing Gutsy on my new desktop? I have just bought a prebuilt desktop (without OS):
Asus P5K (standard) onboard HD Sound 
Core2Duo E6550
Nvidia 8500 GT
2 HD Sata
2 IDE Optic Drives (Master,CD Writer and Slave,DVD)
Floppy

I have flashed the bios with the new 0603 BIOS for that board. 
It has J-Micron which is set to IDE (the alternatives are raid,ahci)
The driver version of J-micron is 1.06.69.

I have tried everything on both Feisty and Gutsy Live CDs. Unabled floppy in the bios, changed J-micron to ahci and raid, it just wont get passed the Ubuntu loading screen after choosing the install option in the bootup. It ends up in a prompt (not a normal prompt, something different that I cant recall whats called).

I really like to install Gutsy on this pc, but it just wont let me. HELP!!!!

---

### Post by Triptoph on 2007-11-09
I have an Asus P5K Deluxe Motherboard as well.  The 64-bit versions do not work for me either, but I found that the i386 version worked fine, have you given that a shot?

Your problem may be different though, as I do not even get a prompt.  Trying to install Ubuntu in any graphics mode with either an Ati X800 or an nvidia 8800 GTS both result in my monitors shutting off with no HDD activity as soon as it tries to load the ubuntu 'wait while we load stuff' screen (and if splash and quiet are turned off in boot options, the system appears to stop doing anything when it tries to load 'squash installer' or something like that).

---

### Post by conphara on 2007-11-09
I forgot mention that I've tried installing both 32 and 64bit, both wont install. The difference is that 64bit shuts off the monitor during the Ubuntu loading bar, 32bit doesnt.
I havent tried the alternative cd, neither feisty or gutsy, only the live cds.
I've tried the no-splash command but I cant remember where it stopped on either 32/64, feisty/gutsy.
I just hope that its something simple that I have to adjust.

---

### Post by Chamelion on 2007-11-09
[HTML] I have just bought a prebuilt desktop (without OS):
Asus P5K (standard) onboard HD Sound
Core2Duo E6550
Nvidia 8500 GT
2 HD Sata[/HTML]
I have the exactly same setup. The 64bit feisty, gutsy version also turned of my monitor. (Asus1680x1050 resolution). I turned the monitor back on after a while and Ubuntu was there, but I had no access to the boot screen options. 
The 32bit options should work without problems though. Have you checked the Md5 sum on the 32bit live cd's? It also might help to use the check for faults with the option provided on the live cd.. I also installed Ubuntu Studio Feisty with the alternate cd. (32bit) Again I had no problems.
There could be a problem with the ISOs.
Maybe you should burn them again with the slowest speed possible and try to install once more. This is the experience I had and I hope that it might help.

---

### Post by conphara on 2007-11-09
Many thanks for the advices but its not burned cds. Yes I have tried the one I burned on the 19'th and with the shipit cds that came with the mail yesterday. Both behave the same.
The checksum matched with the one I burned. No problems there. I havent though checked with the check option in the startup ubuntu menu.
But I really cant believe thats the problem. 
My guess is that it has something to do with the J-micron but I dont know what.
Someone suggested in another thread that you should disable the floppy drive, but that doesnt work for me. Changing the settings for the J-micron doesnt work either, changing it to achi or raid instead of ide.
I havent though tried booting up the live cd with my sata HD disconnected, but if that worked I couldnt use Ubuntu for anything but the live environment.
I am actually sick and tired of this problem and really, really hope that someone out there has the answer...

---

### Post by mozkill on 2007-11-16
make sure you run a memcheck on your RAM.  its also possible that a bad ram sector will crap-out the install, especially if its a 64-bit install.

if that doesnt work then try researching "boot options" just before you start the setup.  there are options that you can toggle that might allow you to get things installed.

---

### Post by Pumalite on 2007-11-16
Here is a guide and a collection of boot parameters that you might want to try:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by conphara on 2007-11-20
Actually I got it working a couple of days ago. It was something simple. Well a part of it was. The IDE cable that I used for my optic drives was an old, but still ok looking, cable but longer than the new cable which came with the pc. The reason was that the new one was shorter and couldnt reach the drives so I used the old one instead. 
The new one did the trick and the live cd loaded perfectly. That part worked. The part that didnt work 100% was that damn jmicron controller. Loading up Ubuntu showed me both optic drives and the two sata drives. After the installation the slave optic drive shows up in nautilus but not in the hardware list. In Nautilus when clicked it says that it doesnt exist. I loaded the module for jmicron before the installation so I was sure that the jmicron was controlling both drives. No problems with the sata drives.
So the conclusion is: sata drives work with only one IDE drive (master) connected. Not the most perfect solution but OK all things considered.

---

### Post by jn25b on 2007-11-29
The Gutsie Live CD just ran install, apt-get update, on the Asus P5K.

I AM having trouble with the VMserver that did run on Feisty.

---

### Post by mozkill on 2007-11-30
I started a similar thread here: [http://ubuntuforums.org/showthread.php?t=627308](http://ubuntuforums.org/showthread.php?t=627308)

---

