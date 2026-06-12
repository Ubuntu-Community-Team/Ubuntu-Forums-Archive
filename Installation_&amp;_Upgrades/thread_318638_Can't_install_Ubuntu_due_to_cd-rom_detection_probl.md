---
title: "Can't install Ubuntu due to cd-rom detection problems"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by wconstantine on 2006-12-14
Hey.
When I try to install Ubuntu (I've tried with Dapper Drake and Breezy Badger) I get a message that my CD-Rom is not a usual one and therefore it refuses to install ubuntu if I don't load the drivers for it. I got a common IDE dvd-rom. :-? 

My computer is quite fresh and I'm currently running Windows XP, and it worked perfectly fine for Windows. I have installed Ubuntu on my CD-Rom before so I don't see where the problem is. The thing that has changed is a major change of my hardware and now suddenly I can't install Ubuntu. When I try to install through 6.06 it doesn't show launch live-cd or so either. There is only Install in text mode or Install in OEM mode. :confused: 

   I got 2gb ram 556mhz. Intel Core 2 Duo E6660 and a neat graphic card too. 80gb HDD and one dvd-rom. I used to have a cd-rom aswell but I unplugged it because I feared the power relay didn't have enough power to support all my hardware. It's 450W. I think it can be that my cd-rom doesn't get enough power because when I burn things in Windows the whole comp laggs down and that's also the case when I use it to read from dvds and cds.
   Still I don't see the problem, it reads from the cd already when it prompts to know what kind of cd-rom I got. Makes no sense.

Anyone with the same problem? Anyone know what to do? 
Thanks. ;)

---

### Post by wconstantine on 2006-12-14
bump

---

### Post by junglistmaster on 2006-12-15
> **wconstantine said:**
> bump
unfortunately you seem to be in the same boat as thousands of others who i gues have an intel type 965 motherboard. even gigabite and via have the same problems. search ubuntu forums and you will find 1000's people with the same prob.
i have spent weeks of spare time tring to find a workaround only to fry my board somehow (prob a good thing) and swapped it for a intel 975xbx2  and now i can install any linux i desire!!!!

---

### Post by wconstantine on 2006-12-15
What a pain. ](*,) 
Thanks for the help, though.

---

### Post by wconstantine on 2006-12-15
Although a bios update might work?

---

### Post by wconstantine on 2006-12-16
Edgy Eft, Ubuntu 6.10, fixed this particulary problem for me. Thumbs up for Linux yet again.

---

### Post by wconstantine on 2006-12-16
Ok this is starting to get really funny now. I installed Egdy Eft but now I get grub error 21 upon booting! =D

Anyone know what I can do to prevent this from happening? I think the problem still is that the kernel doesn't support my intel 965 chipset. Can I update the kernel from the live cd? Can I reach my Windows partition from the live cd so I atleast can copy my work? <.<

---

### Post by Sef on 2006-12-16
Here is GRUB error 21:

> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

You might just check your cables to make sure nothing is loose, but with that motherboard, but think loose cables would not be the problem.

Also if you have enough room on your hard drive, you could dual boot with [Fiesty Fawn]("http://www.ubuntu.com/testing/herd1").  It is not ready for everyday use, but check it and see how it does.

---

