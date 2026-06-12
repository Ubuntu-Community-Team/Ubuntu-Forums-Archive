---
title: "Installing Feisty oon Emachine 333cs"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by dfarce on 2007-08-18
Hello everyone. I have an old Emachine Etower 333cs lying around so I decided to try putting Feisty on a fresh 6Gb HD in it. However, the liveCD refuses to load. I think that this is due to the limited 32Mb of ram. I am going to check out the system requirements for Feisty, but can anyone tell me if maybe the alternate installer might get Ubuntu installed?

---

### Post by merlinus on 2007-08-18
With only 32MB RAM, you will not be able to install any flavor of ubuntu, which includes kubuntu and xubuntu.

Try damn small linux or puppy linux.

-merlin

---

### Post by Gremlinzzz on 2007-08-18
32Mb of ram// I need more power Captain need more Dilithium Crystals

---

### Post by dfarce on 2007-08-19
yeah after looking at the requirements for even Xubuntu I realised that a lowlier version of linux would be needed, so I downloaded the DSL ISO. I wish it didn't look so much like windows 98 though (as I have a 98 CD lying right here). I know im talking in the wrong forum here but does puppy linux look any different from DSL? or would it be possible to change the windows of DSL?

---

### Post by logos34 on 2007-08-19
> **dfarce said:**
> yeah after looking at the requirements for even Xubuntu I realised that a lowlier version of linux would be needed, so I downloaded the DSL ISO. I wish it didn't look so much like windows 98 though (as I have a 98 CD lying right here). I know im talking in the wrong forum here but does puppy linux look any different from DSL? or would it be possible to change the windows of DSL?

You might even check out [Deli linux]("http://delili.lens.hl-users.com/").  I think it's hands-down the lightest distro out there (it'll even run on 486 machines and 16MB ram).  Not sure about the looks though

---

### Post by K.Mandla on 2007-08-19
Is it possible for you to stick some more memory in there? Memory for that machine will be either dirt cheap or hideously expensive, depending on what kind it takes. 

I used to find old eMachine 333s in the recycling yard, and bring them back to life. Ubuntu will run on it, but you've got to get more memory in it, or the installer won't even work (I've tried it at 32Mb, it goes crazy on you. 36Mb is the magic number. :| )

---

### Post by dfarce on 2007-08-20
Well. I will check the kind of RAM and see about prices [actually, it might even be cheaper to buy a new mobo and ram in this day and age]. But I tried using a DSL live cd. It will boot, but freeze while loading. It works fine, saying:

Welcome to DSL etc.
Scanning for USB Devices... Done.
Accessing DSL image at /Dev/sdc0
Total memory found: 29416kB 
Creating /Ramdisk (blah) on shared memory... Done.
Creating directories and symlinks on ramdisk... Done.
INIT: Version 2.78-Knoppix booting...
Running Linux Kernel 2.4.26
Processor 0 is M II 3x Core/Bus Clock 250MHz

and then...
nothing
The text is even color coded, but after it displays that, nothing happens. Nothing else loads, Keyboard doesn't do anything. I am pretty sure that DSL should run because on the site it says it can run on machines with 24Mb of ram.

But I will check out Ram prices, I know that this computer can be upgraded to 128MB (maybe even 256) so I'll jus have to see prices.

---

### Post by dfarce on 2007-08-22
well, the ram is PC66 SDRAM. I checked out my favrite retailer and it was about fifteen bucks for a 128MB stick. so, I decided it would be much easier and cheaper running linux in a virtual PC. I am going to look because I remember something about quemu (MS Virtual PC works for DSL, ubuntu has problems, but I can't get the LAN passthrough to work, meaning so internet and no software packages) so I'll check out various things. any thoughts on a multi linux compatible haredware virtualization software for windows? I know im geting off topic.

---

