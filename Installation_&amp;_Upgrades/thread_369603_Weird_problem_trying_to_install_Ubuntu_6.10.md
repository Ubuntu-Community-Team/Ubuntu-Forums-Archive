---
title: "Weird problem trying to install Ubuntu 6.10"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by JeffH on 2007-02-24
I don't know exactly what the problem is or how to describe it fully. But when I try to run the Ubuntu CD, select "Start or install Ubuntu", it goes to the Ubuntu loading screen. When that finishes, it brings me to a light-brown screen with nothing on it. Then after 20 seconds or so it looks like something tries to pop-up, but something happens. I can see the very top of the window that I assume is what is supposed to pop-up, but there seems to be a graphical error. It won't display the whole pop=up box, it tries to, but the box becomes static looking under it (like a TV with no signal, the white and black feedback you get). I checked the CD for errors, none found, and I tried to start using the safe graphics mode option, and the same thing happened.

It's really hard to explain, I will upload a picture once I can get it off my phone (have to get and install Motorola Phone Tools).

---

### Post by wireddad on 2007-02-24
What type of system are you trying to install on?  What are you running?  Details please.

---

### Post by JeffH on 2007-02-24
I'm on a PC. My specs are:
-Opteron 165
-ASRock dual-eSATA II MOBO (based on ULi chipset)
-2GB of RAM (PC3200)
-200GB SATA HDD (120GB Vista partition, 70GB partition waiting for Ubuntu 6.10)
-GeForce 7800GT

I'm still working on getting the pics off of my phone.

---

### Post by JeffH on 2007-02-24
SCREENSHOT:
[http://img120.imageshack.us/img120/6585/0224071530md9.jpg](http://img120.imageshack.us/img120/6585/0224071530md9.jpg)

It hangs on that, doesn't go any further. Anyone else had this problem?

---

### Post by wireddad on 2007-02-24
I have had similar problems after forgetting to change the burn speed--even  when checking the cd says no problems.  Was the image burned at a low speed?  The livecd should at least run.  Do you have another pc to check the cd?

---

### Post by JeffH on 2007-02-24
I'll burn the CD at a lower speed. ISO burning software is......lacking on Vista. The only good ISO burning software I have found that works with Vista doesn't have speed control. I'll burn it with a different computer at 4x speed and see how it works after that. If I have any more problems i'll post here, thanks for helping me out :)

---

### Post by JeffH on 2007-02-25
I burned it at 4x and it still did the same thing...

---

### Post by ebichuhamster on 2007-02-25
Seem to be expiriencing related problem as previously stated.  Only the live CD doesnt get to the actual interface.  The last page i see contains:

*Prepairing Restricted Drivers [ok]
*Starting basic networking [ok]
*Loading Hardware Drivers [ok]
*Starting PCMCIA services [ok]
PCMCIA not present
Loading manual drivers [ok]
mount: function not implemented
*starting Raid Devices...

There it ends, you can actually hear that the computer stops reading from the live CD.

I allready tried Version 6.1 and I could atually install it, but on reboot I couldn't get it to load again.  

Allready tried 10x for the ISO image on the cd. Same problem

Maybe its a Hardware thing:
(I'm noob so any other info about specific hardware let me know and I ll try to look it up)
AMD Turion 64x2
ATA Fujitsu MHV2120B 120 Gb
1Gb RAM

*HP model laptop so maybe that has something to do with it, hope not.

If this problem may be answered herea t some point, good if not, could anyone point me in the right direction?

---

### Post by mattym on 2007-02-25
> **JeffH said:**
> SCREENSHOT:
[http://img120.imageshack.us/img120/6585/0224071530md9.jpg](http://img120.imageshack.us/img120/6585/0224071530md9.jpg)

It hangs on that, doesn't go any further. Anyone else had this problem?


I am attempting my first Ubuntu Install (6.10) using the ubuntu-6.10-desktop-amd64.iso image and experiencing the exact same issue. Any suggestions would be greatly appreciated :)

System Specs are:
ASUS A8N-E Motherboard
AMD Athlon 64 X2 3800+ 
eVGA 256-P2-N516 Geforce 7800GT 256MB PCI Express
2GB (2 x 1GB) PC 3200 SDRAM
Seagate Barracuda 250GB HD

---

### Post by wireddad on 2007-02-25
Are y'all using the amd64 iso?  I have not installed that version but I'd think it would be the same.  So the livecd will not boot either?  When I had this problem, I had a hardware that the cd did not like - wireless mouse(USB).  Once I'd plugged in a standard USB or PS2 mouse, on my laptop, all was fine.  Then afterwards plug in the wireless mouse and all was fine after install.

---

### Post by mattym on 2007-02-25
> **wireddad said:**
> Are y'all using the amd64 iso?  I have not installed that version but I'd think it would be the same.  So the livecd will not boot either?  When I had this problem, I had a hardware that the cd did not like - wireless mouse(USB).  Once I'd plugged in a standard USB or PS2 mouse, on my laptop, all was fine.  Then afterwards plug in the wireless mouse and all was fine after install.

I am using the AMD 64 ISO, but do have a wireless  mouse....let me give it a shot with a PS2 mouse.

---

### Post by JeffH on 2007-02-25
I too have a wireless USB mouse (Logitech G7). Did the mouse work AFTER you installed Ubuntu (i.e, you just had to install without the wireless mouse)?

---

### Post by wireddad on 2007-02-25
Remember, that the suggestion worked for me.  Hopefully I have at least gave y'all something else to try until more experienced chimes in.  :)

---

### Post by JeffH on 2007-02-25
Well, it didn't work, thanks for the advice anyways, it seemed reasonable. Unfortunately, I don't have a PS/2 keyboard or mouse, so I just switched to a standard USB wired keyboard and mouse and unplugged every other component from my PC and the same thing happened. At this point, I have no idea what the problem could be. The other poster in this thread who had the same problem and myself have extremely similar specs, so that's saying something to me, but I just don't know what the problem is. I've never actually installed Linux successfully (i've tried before. Fedora Core 4 wouldn't install, and OpenSUSE crashed on installation (and continued crashing on installation when I tried to reinstall), and ended up taking my Windows partition down with it)....so I just don't know. I'm starting to think I should just stay with Windows.:(

---

### Post by mattym on 2007-02-25
Similar to JeffH I to continue to experience what seems to be an identical issue. I've tried booting off the CD with just a mouse and keyboard and no other peripherals attached, regardless of the combination the result is always to orangeish screen with what looks like a squished desktop.

Initial Screen
[http://www.mattym.com/downloads/step_1.jpg](http://www.mattym.com/downloads/step_1.jpg)

After Selecting Option 1
[http://www.mattym.com/downloads/step_2.jpg](http://www.mattym.com/downloads/step_2.jpg)

Final Screen
[http://www.mattym.com/downloads/step_3.jpg](http://www.mattym.com/downloads/step_3.jpg)

---

### Post by wireddad on 2007-02-25
I am sorry for not being able to help.  Have y'all tried running K or Xubuntu livecd?  Or the alternate cd's?

---

### Post by mattym on 2007-02-25
> **wireddad said:**
> I am sorry for not being able to help.  Have y'all tried running K or Xubuntu livecd?  Or the alternate cd's?


I appreciate the help and will be trying 6.06 then an alternate CD.

---

### Post by mattym on 2007-02-25
After many failed attempts I decided to just wipe my hard drive and start from scratch...low and behold Im now up and running on 6.06 :) .......should be some fun tinkering with all the new stuff over the next days and weeks.

---

### Post by gwoodard on 2007-02-25
I burned an Ubuntu 6.10 iso to a cd at 1x and had the boot order as follows

ATAPI CD-ROM
Hard Disk
Removable Drive (Floppy)

Anyways, I start the computer and it reads the cd but it does not go to the setup menu

My Hardware Config

Intel Pentium 3 1ghz
512 mb PC133
6.4gb Hard Drive
Onboard video
Onboard Sound
Compaq NetIntelligent NIC
Windows ME

---

### Post by JeffH on 2007-02-25
> **mattym said:**
> After many failed attempts I decided to just wipe my hard drive and start from scratch...low and behold Im now up and running on 6.06 :) .......should be some fun tinkering with all the new stuff over the next days and weeks.

Well, I guess that would be the best option then, but i'm not willing to do that honestly. I'm gonna go try some of the other Ubuntu based LiveCDs, but I would really just prefer the standard Ubuntu...

---

### Post by wireddad on 2007-02-25
> **mattym said:**
> After many failed attempts I decided to just wipe my hard drive and start from scratch...low and behold Im now up and running on 6.06 :) .......should be some fun tinkering with all the new stuff over the next days and weeks.


Great!  The problem could have been that there were still remnants of previous installs.  Thought when you tell it to format the drive it should be ok.  Interesting.  I have notice funny things when I install one distro right over top of another -- eventhough I tell it to format.  Note to self.

---

### Post by wireddad on 2007-02-25
> **gwoodard said:**
> I burned an Ubuntu 6.10 iso to a cd at 1x and had the boot order as follows

ATAPI CD-ROM
Hard Disk
Removable Drive (Floppy)

Anyways, I start the computer and it reads the cd but it does not go to the setup menu

My Hardware Config

Intel Pentium 3 1ghz
512 mb PC133
6.4gb Hard Drive
Onboard video
Onboard Sound
Compaq NetIntelligent NIC
Windows ME

The CD-rom just spin up but no boot screen comes up?  Do you have tweakui installed and the option to auto boot turned off?  Does it do this on other computer?  Can you view the files on the CD in window explorer?

---

### Post by gwoodard on 2007-02-26
> **wireddad said:**
> The CD-rom just spin up but no boot screen comes up?  Do you have tweakui installed and the option to auto boot turned off?  Does it do this on other computer?  Can you view the files on the CD in window explorer?

First Answer, Yes, Second, what are you talking about?, Third Yes, and last, I did it with winace...

---

### Post by JeffH on 2007-02-27
No other LiveCD worked...

Now I have 70GB of nothing on my primary HDD >_>

---

### Post by JeffH on 2007-02-28
So there's no official solution to this problem? Is it my hardware?

---

### Post by JeffH on 2007-03-10
One last bump. Otherwise I will just wait for 7.04 I guess...

---

