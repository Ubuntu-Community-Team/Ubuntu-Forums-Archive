---
title: "Lice DVD fails to load after first page, even safe mode"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by Rorke on 2008-10-14
Laptop, new, low spec (don't yet know all the details)
When I try to boot from the DVD, the orange horizontal bar stops at about an inch, almost immediately.

This happens whether I'm trying from the Live CD, or trying to install from it.

I already have XP on the laptop (but it too had driver problems) and I want to dual boot it.

Any thoughts? Would another distro be worth trying? (Although I'd want to come back to Ubuntu as soon as possible)

---

### Post by overdrank on 2008-10-14
> **Rorke said:**
> Laptop, new, low spec (don't yet know all the details)
When I try to boot from the DVD, the orange horizontal bar stops at about an inch, almost immediately.

This happens whether I'm trying from the Live CD, or trying to install from it.

I already have XP on the laptop (but it too had driver problems) and I want to dual boot it.

Any thoughts? Would another distro be worth trying? (Although I'd want to come back to Ubuntu as soon as possible)

Hi and the specs would help alot. If you have low memory this may cause some issues.

---

### Post by Partyboi2 on 2008-10-14
You could remove the splash and see where it is stopping at. You can do that by pressing F6 at the main menu and removing the word splash.
If it is a low spec machine you might be better installing [[COLOR=Blue]xubuntu[/COLOR]]("http://www.xubuntu.org/")

---

### Post by Rorke on 2008-10-15
(removing splash) it hangs at 
Loading, please wait...

Although it is the cheapest laptop, it is a relatively high spec.
This from the sales site:
"
Screen 		15.4" WXGA X-Brite 1280 x 800 TFT Screen
Processor 		Intel T2370 Dual Core Mobile 1MB Cache Processor
Processor Speed 		2 x 1.73GHz
Memory 		2GB DDR2 667MHz Memory
Hard Drive 		160GB SATA Hard Drive
Drive 		DVD/RW Multi Burner
Modem 		NA
Graphics 		M672 Vista Premium Optimised Graphics
Sound 		High Definition Audio
Speakers 		2 x 1.5 Watt
Floppy Drive 		NA
Memory Slots 		1x DDR2 SO-DIMM
Memory Capacity 		1GB
Audio In Port 		1 x Mic-in
Audio Out Port 		1 x H'phone/Speakers
Networking Port 		1 x 10/100 LAN & 54G Wireless LAN
Serial Port 		NA
Ext Monitor Port 		1 x VGA Port
RJ11 Modem Port 		NA
Power Socket 		AC Power Adapter
TV Port 		NA
USB Ports 		4 x USB 2.0
PCMCIA Port 		NA
Bluetooth 		No
Webcam 		NA
AC Adaptor 		AC Adapter Supplied
Internal Battery 		Lithium Ion Battery
Touchpad 		Glidepad with 2 buttons
Scroll Button 		NA
Dimensions (mm) 		36h x 358w x 258d
Warranty 		12 Mths RTB
Weight 		2.7Kg with battery
OS Compliance 		Windows XP / Vista 
"

Although I don't know how to check, I wouldn't mind betting there is some compatibility issue with low level hardware. It gives the same response wheen trying to boot from an external DVD (USB connected) drive.

---

### Post by Nebutron on 2008-10-15
I don't think low specs is the problem here.  I once had a compatability issue with an asus M2N motherboard that had to do with a "syncing" problem.  It may be worth trying the Alternate Installation CD.  

Also, have you been able to check the integrity of you CD or DVD?

---

### Post by Rorke on 2008-10-15
I've used the DVD a lot of times before, and also I have a CD of just the install that also hangs.
I can get a prompt from a utility disk (Super Grub Disk) and I can run XP ok, although I get driver install problems, hence my thought that it is a new component compatibility issue.

I don't know how to make a USB boot stick, although I've tried. It didn't boot. I don't know why.

---

### Post by Nebutron on 2008-10-21
Hi, sorry no response for a while.  Was out of state on vacation.  I notice that you have indicated you have 2 gigs of ram installed, but also show a machine limitation of 1 gig of memory.

[COLOR="Red"]Memory 2GB DDR2 667MHz Memory[/COLOR]
Hard Drive 160GB SATA Hard Drive
Drive DVD/RW Multi Burner
Modem NA
Graphics M672 Vista Premium Optimised Graphics
Sound High Definition Audio
Speakers 2 x 1.5 Watt
Floppy Drive NA
Memory Slots 1x DDR2 SO-DIMM
[COLOR="Red"]Memory Capacity 1GB[/COLOR]

If this is accurate, I wonder if ubuntu is having difficulty properly addressing the apparent excess memory.  Just a thought.  Don't really know if that would be a problem.  :)

---

### Post by Rorke on 2008-10-22
Heh, Heh! This is copied directly from the dealer's web page. I wonder what it means? I hope it means a typo on their part!! (Should it be 16Gb?) I'll ask them.

---

### Post by Nebutron on 2008-10-22
Yeah,  Probably just a typo. If it shows in XP under My computer>view info as 2 gigs of memory, there is no question.  Then we have to look elsewhere to find your answer.

---

### Post by Rorke on 2008-10-28
Well, the laptop is definitely 1.87 Gb RAM, T2370 1.73GHz Dual processor.
It won't accept 8.10 either.

Any thoughts?

---

### Post by Nebutron on 2008-10-28
> **Rorke said:**
> Well, the laptop is definitely 1.87 Gb RAM, T2370 1.73GHz Dual processor.
It won't accept 8.10 either.

Any thoughts?

Hmmm.  Have you tried the alternate install CD?  It is desiged to aid installation on low-memory (<256megs) units, but may give you a different result.  

Another thought would be to set up your partitions using Parted Magic and then try the alternate install CD.  Here is a link to Parted Magic in case you want to try it out:  

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

---

### Post by Rorke on 2008-11-02
OK, moving on to 8.10, installed within windows.
Booting in verbose mode I get:

2.077930 ACPI: CPU1 
2.078147 processor ACPI0007:01 registered as cooling_device1
2.078581 ACPI: processor {CPU1} (supports 8 throttling states)
2.078906 Marking TSC unstable due to TSC halts in idle

and permenantly hangs here.

---

### Post by Rorke on 2008-11-02
Booting in no APCI mode boots all the way to a prompt! :-) but with no graphics.
X server failed to start after 60 seconds.
Booting in safe graphics mode is the same as above, normal boot.
In no ACPI mode, 'Unable to set the system clock' is flagged up.
Also, there is a large pause on 
'Attached scsi removable disk
Attached scsi generic sg2'



So I get to a command line propmpt.
Any good commands?

---

### Post by Nebutron on 2008-11-02
Here is a link to another thread that may be of interest, though it does not really spell out a solution.  It appears it may be worthwhile to spend some time looking at the bios to see if you can tweek something related to vista to allow your graphics to work.  [http://ubuntuforums.org/showthread.php?t=952457](http://ubuntuforums.org/showthread.php?t=952457)

---

### Post by Rorke on 2008-11-02
He doesn't say how to solve the problem. I'm using 8.10 now.
I just pm'd him.
Are there any good debug cli commands that you know might help?

---

### Post by bl00d666 on 2008-11-02
hi guy,
i got a similar problem while trying to make a fresh install of intrepid ibex on my pc. my old hardy just cease to work and when i try to boot from live cd i got a bunch of error. so i try a **** load of command and option single and combined (noapic, noacpi, nolapi, irqpoll, noirqdebug, etc...) and no one work for me each time i got different bug like kernel panic, segmentation fault etc.. i finally put my 2 old 512mb ddr memory stick that i change recently for 2 1gb ddr2 memory stick and finaly he manage to boot normally on intrepid ibex without any option. i install it and it work real fine now, but i dont have my new ddr2 memory. so whats with ubuntu and ddr2 support ??? does anyone can answer that. does the alternate cd lets us install some support for it???  

p.s. sorry for my english, i speak french

---

### Post by Partyboi2 on 2008-11-02
> **bl00d666 said:**
> hi guy,
i got a similar problem while trying to make a fresh install of intrepid ibex on my pc. my old hardy just cease to work and when i try to boot from live cd i got a bunch of error. so i try a **** load of command and option single and combined (noapic, noacpi, nolapi, irqpoll, noirqdebug, etc...) and no one work for me each time i got different bug like kernel panic, segmentation fault etc.. i finally put my 2 old 512mb ddr memory stick that i change recently for 2 1gb ddr2 memory stick and finaly he manage to boot normally on intrepid ibex without any option. i install it and it work real fine now, but i dont have my new ddr2 memory. so whats with ubuntu and ddr2 support ??? does anyone can answer that. does the alternate cd lets us install some support for it???  

p.s. sorry for my english, i speak french
Have you tried doing a memtest when using those ddr ram?

---

### Post by bl00d666 on 2008-11-02
yes, i make a first memtest with a 7.10 live cd and it failed but after i read that 7.10 memtest doesnt support ddr2. i try 8.04 live cd memtest after that and its succeed very well. my memory are brand new like 1 month old so i doubt its a probleme with them. im on dual boot with winxp and its work very well with my ddr2 mem. i search if ubuntu support or not ddr2 and its appear to be working for some people but i dont understand why its fail with me

---

