---
title: "New build"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by Howy on 2010-06-30
I built a computer just today. Its an ASUS-motherboard, AMD Phenom II X4 processor, 6Gb RAM, integrated ATI Radeon 4200 graphics card and an ATI Radeon HD 5750.
I am trying to install Ubuntu 10.04 64-bit on it.
However, when i insert the disc, and fire it up, the screen stays in standby mode. But the computer itself starts all fans successfully and the motherboard's LED is green.
What do i do?
I have connected a VGA cable to the integrated card.

---

### Post by mhgsys on 2010-06-30
First of all; try connection the cable to the other card...
Could be that bios is setup to use agp instead of integrated.
:p

---

### Post by Howy on 2010-06-30
I forgot to mention a detail... the HDD is completely new, nothing on it, this is first run.
I dont know if the BIOS is pre-installed. All i know is that the computer is pretty much empty, and possibly without a BIOS.
Should i use a disc that came with the motherboard?
It doesnt bring up any screen either, though.
Would it help if i set the DVD-reader to be the first SATA?

---

### Post by mhgsys on 2010-06-30
ERH.. 
Without a BIOS you say?

You should be able to acces BIOS even if no HD or DVD is installed...

When you turn on the computer, you must see some POST now don't you?

if not; then you should here some beeps.. and probably your RAM is not correctly installed or you misplaced the AGP card.

During POST, you'll see something like, press f12 for boot menu and f1 (or f2) voor bios... but this variates... a little.

Anyhow... you get my drift..

sure you can try to put the motherboard dvd in but I never heard of a computer without BIOS.. 
accept for some old compaq laptops... .. with floppy drives..

ps: this might be useful for you
[http://www.hardwarecanucks.com/forum/guides-how-tos/914-10-step-no-post-bios-recovery-guide.html](http://www.hardwarecanucks.com/forum/guides-how-tos/914-10-step-no-post-bios-recovery-guide.html)
(*NOTE that you can also reset CHMOS by taking out the battery on the motherboard for a while..

---

### Post by Howy on 2010-06-30
I dont really know, but there is nothing appearing on screen.
Yes, it might be the RAM. I was kind of skeptical about it. It said something like 10600 on the box, but i dont know what it means.
The motherboard supports 1066Mhz and up to 1600 when overclocked.
I just hope it doesnt mean Mhz, else i will complain to the computer-store for not telling about incompatibility between parts.

EDIT: It shouldnt be any incompatibility with the RAM. Its the right frequency, but i dont know if it supports 3x of the chip type i have. It says "2048Mb", but on others it says inkit of 3 or 2.
Can this be a problem?
Also, is something wrong if a fan inside has a pattern of power going up and down?
Its really hard to know whats wrong here...
All parts seem compatible.

---

### Post by CyClyst on 2010-06-30
where did you get your computer from?

I bought my computer without an OS but it still had major things (like BIOS) working.

---

### Post by mr clark25 on 2010-06-30
does the computer display when you dont have the disk in?

if it doesnt, it is a hardware problem. (i am very good with hardware and troubleshooting it, as are many others,)

---

### Post by Howy on 2010-06-30
> **mr clark25 said:**
> does the computer display when you dont have the disk in?

if it doesnt, it is a hardware problem. (i am very good with hardware and troubleshooting it, as are many others,)
Nope, but i hope you know lots. Because i want to get this thang running at least tomorrow. (Right now i am about to go to sleep, but typing from a Linux-powered phone. (N900))
Its mostly the same whatever i do, but the disks do work some.
So, this is status:
-RAM-chips should be compatible, they fulfill all requirements fully. But i might check if it helps to have only 1.
-The CPU and fan seem ok.
-I believe all power supply is ok.
-The GFX-card is connected through PCI-E x16 and has power. Fan runs.
-The storage mediums are all SATA-based, no IDE-connected storage.
-HDD is set as SATA1, DVD/CD-drive is SATA2.
-When ejecting the DVD/CD-drive, the computer tries to pull it back in.
-There is a fan somewhere having a weird pattern of effectivity, its wave-like.
I hope this info is helpful. :)
I'll be thankful for any help on this.

And i think it does have a BIOS, please bare with me, i was just doubting, this is the first time i do this.

---

### Post by mhgsys on 2010-06-30
> **Howy said:**
> 

 It shouldnt be any incompatibility with the RAM. Its the right frequency, but i dont know if it supports 3x of the chip type i have. It says "2048Mb", but on others it says inkit of 3 or 2.
Can this be a problem?
Also, is something wrong if a fan inside has a pattern of power going up and down?
Its really hard to know whats wrong here...
All parts seem compatible.

Does it seem normal to you when a fan inside has a pattern of powering up and down?

:-)
Time to strip her down , 

remove the agp card;
connect the vga cable to the integrated card
disable the hd, remove cables from motherboard  
disable the dvd remove cables from motherboard
Test al ram modules one by one

When you get a post; great.! you'll know it's working.. build it up again; 
piece by piece.
until you locate the error.
If any.

edit;
[quote=Howy]And i think it does have a BIOS, please bare with me, i was just doubting, this is the first time i do this.[/quote]

 here's an example of a BIOS
[http://www.google.com/images?client=ubuntu&channel=fs&q=BIOS&oe=utf-8&um=1&ie=UTF-8&source=og&sa=N&hl=en&tab=wi](http://www.google.com/images?client=ubuntu&channel=fs&q=BIOS&oe=utf-8&um=1&ie=UTF-8&source=og&sa=N&hl=en&tab=wi)

---

### Post by Howy on 2010-06-30
Will try it tomorrow. I really appreciate your help. ;)

...Is something wrong when i dont get POST when trying all RAM-chips?
It doesnt show up, its mostly the same.
Nothing shows up on DVI, either.
Any idea of what can be wrong? I do hope the motherboard isnt broken. :(
Are there any essential things you have to do when installing a motherboard besides inserting 1 big and 1 small power cable and connect the front IO panel + installing the CPU and fan?

Yes, i could try resetting the BIOS. It will only reset to factory settings, right?
And not wipe the whole ROM?

I feel extremely stupid right now... my only problem was that i forgot to plg in the ATX12V! *blush*

Now that i got the BIOS working, i got a problem with Ubuntu. When its inserted, i get to a purple screen where it says:
"I/O error
Error reading boot CD"
And there is a Reboot-button.
Should i burn a new disc?
And should i use a DVD or stay with CD?

---

### Post by mhgsys on 2010-07-01
I always use dvd's, but should make no difference.
I guess..

anyway'
burn a iso with brasero
(burn image)

In this link you can click on show me how, and select the OS your using to burn the iso, or make an usb stick.
(scroll down to step 2 and click show me how)

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

