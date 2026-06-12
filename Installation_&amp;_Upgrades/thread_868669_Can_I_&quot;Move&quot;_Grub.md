---
title: "Can I &quot;Move&quot; Grub?"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by fl_archaos on 2008-07-24
Hello,

I installed ubuntu on an external usb drive.  When it came to partitioning, being a newbie, I made sure in my paranioa to make my internal drive unused.  I think this means the bootloader has installed to the external drive - everytime I start without the usb drive attached grub fails.  As a complete newbie, will reistalling ubuntu to this partition of the external drive mean I can "write" grub to the boot section of my internal drive?  Or is there a relatively simple way to "move" grub (and good first-blooding on linux)?

Many thanks for any help, I've been on a 24hr head-scratch-athon.

Cheers
Nicholas

---

### Post by coffeecat on 2008-07-24
Your problem is that grub stage 2 and the menu file - /boot/grub/menu.lst - are on the external drive.

Explanation - grub stage 1 is in the mbr, the first few hundred bytes of the master hard drive. It replaces the code that Windows would have put there. There are only about 400 bytes, and all it does is to call up grub stage 1.5 (about 8 Kb) which is written to an otherwise unused portion of the hard drive, near the beginning, just after the partition table. Stage 1.5 in turn calls up stage 2 which is why you get a failure when your external drive is not attached.

I applaud your caution (I wouldn't be so impertinent as to call it paranoia) but, as you can see, some parts of grub **have** been written to the internal drive, which means you have to repair the mbr in the unlikely :wink: event of wanting to ditch Linux.

How to get around it? You need to create a small partition, formatted ext2 (it doesn't need the journalling of ext3) on your internal drive to hold the files necessary for grub to run completely. Then you have to reinstall grub to the mbr so that it calls up the relocated stage 2 - this is fairly straightforward. **Or** - and probably simpler - now you realise you have got some of grub on your internal drive, and you'll need to put the rest on the internal drive anyway, start over by resizing your Windows partition and reinstalling Ubuntu, but this time to the internal drive.

I'll leave those thoughts with you. If you want to know how to make a special grub partition I could help you. I am sure that there is a howto somewhere on this forum, but I don't know of one. But by posting I've bumped this thread for you and someone else may be able to point you to a method. Or they may have better ideas.

**Edit:** I was assuming in writing the above that the BIOS is set to bootup from the internal drive which means that it reads the internal MBR. If it's set up to bootup from the external drive, then all the stages of grub should be on the external drive and you shouldn't get a grub error (I presume that's what's happening) when you boot up without the external drive. The BIOS should then just boot Windows up as normal from the internal drive. Perhaps you could clarify which - it's pointless my speculating further.

---

