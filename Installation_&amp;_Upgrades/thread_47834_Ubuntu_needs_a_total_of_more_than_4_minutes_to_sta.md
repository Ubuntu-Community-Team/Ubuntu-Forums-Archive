---
title: "Ubuntu needs a total of more than 4 minutes to start"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by jon_gunnar on 2005-07-10
I have tried to look around to solve this without luck.
I installed ubuntu on a machine with this spec:

Asus A8N-SLI Deluxe nforce4 motherboard
1Gb ram
HD1 is a Samsung spinpoint P120S SATA2 used for XP
HD2 is a Samsung spinpoint P80SD SATA2 used for Ubuntu
NEC DVD burner at primary pata port.
Graphic card Asus Geforce 6600 PCIe card.
AMD 64 3500+ prosessor
Linux ubuntu 2.6.10-5-386

After post, grub starts with this message:
 "Grub loading" Uses 2.10 seconds (ca) here

Then the menu comes up, if I chose to start Ubuntu it will roll out the kernel version etc and then it stops for another two minutes+ at the boot

Eventually it starts. The same happens if I start xp. Then the screen is blank around two minutes before the xp boot logo starts up. Just for the fun of it I tried the AMD64 version of Ubuntu, and it were the exact same sequence there.

Is there something obvius I have overlooked? I would be very grateful for any tip to help out with this.

---

### Post by emmet on 2005-07-10
Do you have your network configured correctly? This might be causing services to time-out at boot-time.

This might help:

[http://www.ubuntuguide.org/#troubleshooting](http://www.ubuntuguide.org/#troubleshooting) 

Cheers

Emmet

---

### Post by jon_gunnar on 2005-07-10
[QUOTE=emmet]Do you have your network configured correctly? This might be causing services to time-out at boot-time.

This might help:

[http://www.ubuntuguide.org/#troubleshooting](http://www.ubuntuguide.org/#troubleshooting) 

Cheers

Emmet[/QUOTE]
The network works like a charm, an even if that had been faulty it should not take over two minutes to get to the grub boot menu?

---

### Post by emmet on 2005-07-11
You're right. It shouldn't take that long. Mine goes through the BIOS bit and then straight into Grub. Max about 10 seconds.

Sorry, I can't work out what's going on. I thought it was post-grub problems when Ubuntu was starting up. 

There is some interesting information here thought about GRUB polling for SATA drives that don't exist...

[http://forums.fedoraforum.org/archive/index.php/t-2034.html](http://forums.fedoraforum.org/archive/index.php/t-2034.html) 

I don't know if this helps or not. 

Emmet

---

### Post by fedemw on 2005-07-11
hi

well i had have the same problem. my ubuntu stops at booting, searching for something than i dont remember....

i installed ubuntu 5.04 for x86 processor (i also had a amd 64 3000+) and its working fine now.

---

### Post by jon_gunnar on 2005-07-12
[QUOTE=emmet]You're right. It shouldn't take that long. Mine goes through the BIOS bit and then straight into Grub. Max about 10 seconds.

Sorry, I can't work out what's going on. I thought it was post-grub problems when Ubuntu was starting up. 

There is some interesting information here thought about GRUB polling for SATA drives that don't exist...

[http://forums.fedoraforum.org/archive/index.php/t-2034.html](http://forums.fedoraforum.org/archive/index.php/t-2034.html) 

I don't know if this helps or not. 

Emmet[/QUOTE]

After a lot of frustrated thinking, I started to have a closer look at the hardware.
After some work I found out that if I removes everything from the first onboard usb port everything works. No delays. So the problem is solved kind of.
Thanks for your'e help.

---

### Post by emmet on 2005-07-12
I know that this suggestion is going to be tedious, but now that you've found a 'cause' for your problem how about finding the root cause.

What did you have hooked-up to that USB port?
Does everything work when connected to other ports?

Cheers

Emmet

---

### Post by arunsub on 2005-07-12
I had similar problems with Windows XP (Dual boot). I have 4-1 card reader connected to my USB port and if i have a compact flash card inserted in it at the time of booting, the system either hangs or says booting with out doing anything. If i remove the card and boot, it works. Also, If my external hard drive connected to USB port is on, then i get error while booting (forgot the error message) though my external hard drive is at the end of the booting list. If i switch it off, then it works fine.

---

### Post by coolclassic on 2005-07-12
With USB devices connected to your computer at boot time can cause the process to slow down, this is mainly due to modules being loaded if you have more than one USB device attached their could be many modules loading. If this is the case you may wont to start these modules after Ubuntu has started.

---

### Post by jon_gunnar on 2005-07-13
[QUOTE=emmet]I know that this suggestion is going to be tedious, but now that you've found a 'cause' for your problem how about finding the root cause.

What did you have hooked-up to that USB port?
Does everything work when connected to other ports?

Cheers

Emmet[/QUOTE]
The cause of the problem is the usb port. If I connect anything to this particular port, the system boot slows to a crawl. Have tested with everything from scanners, card readers to an bluetooth dongle. On that port, no good. Connect the same equipment to any other port, no problem.

And the hardware summary in xp shows a problem there to. May be as simple as a fault with the motherboard.

---

