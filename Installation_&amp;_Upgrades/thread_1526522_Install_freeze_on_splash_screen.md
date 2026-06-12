---
title: "Install freeze on splash screen"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by TheNTW on 2010-07-08
Hello everybody,
I have failed to install kUbuntu for a several days already, so I am currently on SuSE (hate it, love ubuntu...). 
I don't know what is wrong with my PC, but something ain't right. 

I tried:
1st: Installing kUbuntu x64 - Result: Freeze on loading screen (I think..don't even remember anymore :) ).

2nd: Running Live CD ("Try Kubuntu") - Freeze on splash screen, at the Hard Disc icon (can't get past that one).

3rd: Installing Ubuntu x64 with Unetbootin - (GNOME variant). - I get a nice graphic card error, can't unerstand anything - screen messed up.

4th: Installing Ubuntu x86 with Unetbootin (GNOME) - same as 3rd time.

5th: Decided that maybe something was wrong with the download. Downloaded kUbuntu via torrent. Installed with Unetbootin in a flash - no change.

6th: Installed SuSE

7th: Downloaded kUbuntu x86, burnt, tried installing, back to 1st step.


Is this an infinite loop ?
Hardware specs:

250GB x 2 Seagate Barracuda ( I had them connected in a RAID0 via bios previously(Windows 7), had trouble installing suse because of this, but I deleted RAID information and disabled raid in BIOS setup )

GeForce 9800 GX2
Quad 2 Core 2.66
4 GB unbuffered ram ( 4 x 1 GB)

Help.

---

### Post by ronparent on 2010-07-08
Your problem is most likely a graphics driver incompatibility. But to cover all possibilities, you should first try to boot a live cd session. Hit <f6> when the boot menu on the live cd is displayed and start by selecting the <f6> nomodeset boot option. This will likely fix it to boot, but, you may have to try cycling through one or more of the others to find a combination that will allow your system to boot. Also, delete quiet splash from the boot line displayed after hitting the <f6> - this will allow the boot messages to be displayed and give you some hint at what is stopping a successful boot. Keep posting your results here.

---

### Post by TheNTW on 2010-07-08
No Idea what is wrong. 
If I get past "Setting sensor limits" - I am stuck at the splash screen. Changing boot modes didn't help :(.

---

### Post by davidmohammed on 2010-07-08
suggest Press F6 - at the bottom is the boot string.

add before quiet splash --

nomodeset noapic nolapic acpi=off quiet splash --

then choose "try without installing" - can you get to the desktop?

also try the above without quiet splash - should give you a better idea where the boot is failing.

if you can get to the desktop, reboot but try and remove one or more of the extra options.

---

