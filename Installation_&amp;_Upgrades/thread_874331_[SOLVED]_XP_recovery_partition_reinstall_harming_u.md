---
title: "[SOLVED] XP recovery partition reinstall harming ubuntu partition?"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by Mic_Droz on 2008-07-29
Hey Guys, 

Just a question regarding an xp re-install...

I know there are other threads, but I don't think they've answered quite what I wanted to know...

I've got ubuntu and fedora 8 tri-booting with xp on my Acer laptop from 2 years ago. In the last few days, i've wanted to do some house keeping - ie, get rid of fedora 8 (which was nice, but ubuntu is doing some things I couldn't pull off with FC8) and reinstall windows because its just not running the way it used to (well, what do you expect after 2 years?).

I'd love to wipe the whole thing and then install XP as a virtual machine, but I can't sync my iPhone through a virtual machine (yet), so a real reinstall is the only way...

I don't have the XP install disks, because ACER don't deem them useful enough to package. So i've got the recovery partition, which I'm willing to use... but there are some questions I have before I take the plunge...

If i do the recovery, will that wipe my ubuntu partition? Is this going to reset my computer to *exactly* the way it was when i received it, or do I have some sort of choice about which partitions get violated?

And secondly... the Activation/product code. is this the same thing? I've got a little sticker at the bottom of my laptop, I never needed to enter it - nor did I need to activate my laptop - it was already done so. Am I going to run into trouble? or is it all OK because its the same hardware?

And thirdly - I guess I'm going to have to install grub on the mbr again? or does xp do something different, like leaving my boot sector the way it is?

Thanks for any suggestions or abuse, all is appreciated and graded. 

Oh yeah, I have the GParted Live disk ready to go, i've made a bootable cd of the "super Grub disk" (sounds great, huh?) and I've got the ubuntu 8.04 disk just incase that's the best way to fix the bootloader...

---

### Post by Mic_Droz on 2008-08-01
Well, I think I answered my own question, with a little old fashioned "just close your eyes and hope for the best."

For anyone that wants to know, my Recovery Partition cleared the C: drive, leaving XP in the state it was when it left the factory... without doing anything to the boot loaders, or my linux partition. The only thing it did do was revert the windows partition back to fat32, so I think i'm going to NTFS it again.

Just as an interesting aside, I'd downloaded avast! for windows through linux, installed it straight away - and it found a boot-time scan virus!! windows hadn't even been on the internet yet!! sigh... I hope someone works out a real way to sync the iPhone with linux, that'll be grand...

---

