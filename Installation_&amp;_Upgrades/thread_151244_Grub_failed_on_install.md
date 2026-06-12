---
title: "Grub failed on install"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by GiZ on 2006-03-27
I have just installed Ubuntu on a partition that was previously Fedora  I had no troubles until it came to the section where it loads Grub.  at 50% it fails and gives me the choice to continue or try again.  I tried a second time no luck so I continued.  This machine has Xp on the first partition and Ubuntu on the second.  I have tried several things I have found on this site but have had zero luck so far.  Any ideas??  All help will be appreciated.

---

### Post by SamTheShaman on 2006-03-27
I get the same thing. I have tried everything I can think of for the past 2 weeks to install Ubuntu. Tried Breezy first but it has a problem with mount CD. Nobody figured that one out.
So I gave up and tried Dapper I love it. But forget about installing it. Install goes smooth until.
Grub installation Failed. Continue anyway? 

I have tried everything. Even completely wiped every thing off the hard drives. With XP or without, it's the same problem. I figured it might be my MBR so I did a Dban nuke. Completely wiped everything off the computer. Still same problem.
Too bad ubuntu seems really nice, but I guess some of us are stuck with windoze. Until the bugs are figured out.

---

### Post by GiZ on 2006-03-27
I have been most impressed with Breezy and am running it on 2 other machines.  Just so happens I wanted to replace Fedora on my work PC (Yeah the boss ain't happy) and I can't get past the grub>.  If I could at least mount maybe I could try something from inside.

---

### Post by GiZ on 2006-03-27
Well I just tried using the live cd to restet grub.  No joy.  I wonder if I need to completely remove the partition and then resize the windows partition.  I don't need 37GB for Ubuntu. Then run windows setup disc and do a fixmbr.  Then try a new install tomorrow.  I'll let ya know how it goes.

---

### Post by hotani on 2006-04-06
same problem here. I even had it installed at one point on the brand new drive, but mucked it up when I tried to get Windows going on the same drive. I got windows to install, then grub wouldn't let me see or boot to it. After that, I reloaded the dos boot partition to bypass grub which worked, but now I can't get Ubuntu to reinstall because it can't write to it anymore.

My theory is that somehow windows/dos/nt or whatever is writing the boot loader is locking it so Ubuntu cannot write to it. Ever.

I've done all the mbr, fdisk, fixboot, bootcfg /rebuild, but no go. At one point the disk wouldn't load anything and I had to go into fdisk and reactivate the windows partition. 

This has been hell. It wouldn't have been nearly as bad if I didn't need to dual boot. I've really run out of ideas. Ubuntu looks good but the whole dual installation part seems to be a weak point.

---

### Post by Herman on 2006-04-06
> My theory is that somehow windows/dos/nt or whatever is writing the boot loader is locking it so Ubuntu cannot write to it. Ever. There are anti-virus settings in some computer's BIOS's that prevent anything from being written to the boot sector or MBR to keep out 'boot sector' viruses, and they will also prevent GRUB from being written to the boot sector (MBR) too. You should be able to turn that off before you begin your install.

You can still install Ubuntu even if you cannot install GRUB to MBR. You can use the GAG boot manager and [install  Lilo to your Ubuntu partition]("http://ubuntuforums.org/showthread.php?t=96920") instead, or GRUB to a boot partition. GAG can boot Windows and Ubuntu from a floppy disk, a CD, or install on your MBR and the first track of your hard disk if you prefer. You should give GAG a try if GRUB doesn't do the trick for you, GAG is pretty good.
[CENTER][Click here for GAG/Ubuntu info.]("http://www.users.bigpond.net.au/hermanzone/p12.htm")

Or you could install GRUB to a floppy disk instead of to MBR during your install, that would be another possibly  good  solution if you can't get GRUB to install to MBR, or don't want to.
[/CENTER]

---

