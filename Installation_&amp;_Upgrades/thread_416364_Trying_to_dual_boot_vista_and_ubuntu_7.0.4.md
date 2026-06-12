---
title: "Trying to dual boot vista and ubuntu 7.0.4"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Darrell262 on 2007-04-21
having a heck of a time trying to install ubuntu on my computer. Lost my raid array when I installed ubuntu to a 320 gig storage drive (I boot my raid array for vista)

So I gave up on raid for a bit, 

I want to Install Vista and ubuntu on 2 seperate drives. 

Drive 0 is a raptor 74gig
Drive 1 is a raptor as well and i have 2 320gig hd's (storage)

I want to install vista to one drive and ubuntu to the other raptor. 

So far having no luck.

Ideas?

I installed vista first on the first drive and then after installed ubuntu on the second drive. I can't boot into ubuntu. 

Then tryed re installing, vista freaking out, wont install into drive 0 anymore, I wipe that drive, and wipe drive 1 (ubuntu, ) and now windows will install to drive 1 now. tryed that, installed vista to drive 1 and then after installing ubuntu to drive 0.

before I try installing a few more times I thought I'd ask you guys for help.

Save me some time.. 

Oh, and I am running 64bit vista, and I can get 32 bit ubuntu to boot and install but 64bit ubuntu wont install (black screen) I have a intel duo core 2 cpu :-)  ???

---

### Post by jdong on 2007-04-21
So your Vista is on a RAID array, but Ubuntu is on a non-RAID?

That puts you between a rock and a hard spot, because Ubuntu's bootloader (GRUB) cannot understand BIOS fake RAID's. Hence it's unable to locate Vista in order to dual-boot it. I'm not sure of any reliable solutions to get this working.

My best guess... please don't try this unless you are confident of your Linux skills.... is to extract a grub MBR into bootsect.dos and have the Vista bootloader try to load that. Anyone have experience with this situation?

---

### Post by Darrell262 on 2007-04-21
No, I turned off my raid drive. I am not using raid anymore.

---

