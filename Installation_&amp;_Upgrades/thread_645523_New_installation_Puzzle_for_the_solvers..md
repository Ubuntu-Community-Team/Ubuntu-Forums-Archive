---
title: "New installation Puzzle for the solvers."
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by gkasinath on 2007-12-20
Hello all, 

Here is something (nothing short of a puzzle, imho) I have been trying to solve. 
Backgound: 
Running an existing Gutsy on an internal HDD. 
Bought a new HDD, so moving the existing HDD to a USB enclosure. 

Problem: 
Booting off the USB enclosure with existing Gutsy installation.

Verbose; 
I had Gutsy running on my internal notebook HDD. I bought a new hdd and am installing ubuntu afresh on the same. But I dont want to lose the data and my existing installation. So I moved the HDD to an external USB enclosure, hoping to boot off that on my Desktop (which runs only Windoze XP).

When I tried booting from the USB, theGRUB started, and then nothing happened. Only a cursor in the top left of the screen blinking for over an hour. 

My desktop has a dual head, while the existing ubuntu wasnt configured to run dual head. Further, the resolution on xorg.conf (for my notebook) was less then the resolutions on the dual head. BTW, each head runs a different resolution, due to difference in screen size. 

What am I missing? 

Further, Id like to note that the Ubuntu 7.04 and 7.10 CDs that I received dont boot. They run on XP but my 6.06 which I have finally managed to install cant read them.. 
error is: 
[17180221.808000] ide: failed opcode was: unknown
[17180221.808000] end_request: I/O error, dev hdc, sector 0
[17180222.852000] hdc: media error (bad sector): status=0x51 { DriveReady SeekCo mplete Error }
[17180222.852000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x 03 }


Cheers
Gautham Kasinath

---

### Post by gkasinath on 2007-12-21
bump.. no one interested in a puzzle or has it been solved already? 

I sure couldnt find its solution on the forums or google, care to share a link or two??!

Gautham Kasinath

---

### Post by gkasinath on 2007-12-24
bump again.

---

### Post by K.Mandla on 2007-12-24
Does Grub appear at all when you boot from the USB drive? I'm thinking the drive settings in Grub will only apply to that machine, and if you've put a new HDD in the machine, it will need Grub installed with a pointer to your USB drive to tell it where to find Ubuntu. 

As a different idea, I would install some sort of system on your new drive then connect it and copy your files off the old one. 

Did I answer your questions at all? :???:

---

### Post by gkasinath on 2007-12-30
Hey Mandia, 

Thanks for your reply. I did get GRUB starting up, but then it would just hang after that. I have anyway re-installed 7.10 fresh wiping all data from my HDD which I wanted to preserve. 

I have now started running into problems with Ubuntu and X300 driver for Dual Head + compiz. I must admit, whilst I was impressed with Ubuntu (using since 6.06) on my notebook, I am completely annoyed with getting it working on my desktop. 

Gautham Kasinath

---

