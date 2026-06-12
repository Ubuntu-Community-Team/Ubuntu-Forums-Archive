---
title: "How Feisty Installer broke my hardware RAID-0 Array"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by mephistofun on 2007-05-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/112239](https://bugs.launchpad.net/ubuntu/+bug/112239) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just tried installing Kubuntu Feisty Final on my older Windows box, which has a hardware RAID-0 array on my onboard HPT370 controller.  I boot Windows from a 40gb hard drive on the primary IDE channel.  I opened up 16gb of space on that hard disk and partitioned it using the Feisty installer, which went off without a hitch.  

Only weird thing was that it detected the Primary boot hard disk as SCSI0 and it showed the RAID hard disks separately as hda1 and hda2.  Hmm...  Oh well I didn't plan on using that array in linux quite yet, and I didn't modify anything, so it's OK...right?  Quite wrong!  Next time I booted, the Highpoint controller screamed at me about my BROKEN RAID-0!

Hide the array, boot anyway...lo and behold, no GRUB!  Windows boots right up.  Ubuntu installed to the primary disk alongside windows, all right, but GRUB just went and installed itself all willy-nilly into the MBR of hda1 instead of the disk where I installed ubuntu (and where the XP bootloader resides).

Oh crap, I've really done it now...  That's EXACTLY what I get for using a damn raid-0 array to store files that haven't been burned to DVD yet.  I would still be really pissed off at myself if I hadn't figured out how to restore it already (see bugreport comments for fix).

I understand that this probably isn't anyone's fault but mine.  However, it would have been nice if the installer had simply *asked* me which physical disk to install GRUB to before it wrote anything.  I guess I should have unplugged the RAID disks before installing..

Anyone have a similar story?

--Christophocles

---

### Post by msquito on 2007-05-08
yes!  
nearly exactly what happened to me (although I'd already backed data up) - I too ended up with a broken stripe for windows.  I just scrapped it and figured it was time for a maintenance reinstall but now I repartitioned all (3) drives and decided to scrap the stripe (at least for now) and install singularly onto one of the (3) 40gb ATA 133s - here's the trick tho, my (3) 40s are all connected via the highpoint RAID/ATA133 controller not directly to the board (CD drives in the IDE channels) anyhow when installing win2k, it gives me a chance to install a 3rd party RAID driver which gives access to these drives but I'm not sure how to do that while installing Ubuntu.  (that may be the mother of all run-on sentences)  Any insight to lend?  

tia
msquito

---

### Post by ibender on 2007-07-21
This exact thing also happened to me. I am now attempting a fix. This is going to SUCK.

---

