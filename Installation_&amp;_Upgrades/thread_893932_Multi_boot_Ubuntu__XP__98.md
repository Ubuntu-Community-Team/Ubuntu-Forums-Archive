---
title: "Multi boot Ubuntu / XP / 98"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Whydoe on 2008-08-18
I'm setting up an old computer for my son who likes the older games as well as new.  And also, I just want to see if I can do it without too much hassle.  
I'll be using 3 hard drives.  1 for each OS.  Since I already have a hard drive with 98 as the default OS, I'm going to use that to start.  Then, install XP so that it will recognize the other partition and dual boot that.  Then, I have a copy/ghost of Ubuntu on another hard drive.  I'll obviously have to set up so Grub is loaded on the MBR and I know how to get that back up and running using setup (hd0) etc.  
My question is, will I need a separate entry in the grub / menu.lst for both WinXP and Win98?  Or will just the WinXP entry be suffice since, I believe, XP would retain the Win98 partition setup when I select it from menu.lst? 
Sheesh, the things you do for your kids.  ;)

---

### Post by marine63 on 2008-08-18
you could put win98 under virtualbox that runs and install under linux and windows xp.
dosbox is a emulator that can run dos games
grub once reinstalled with live cd it should have option for windows bootloader option and then it'll go to option for xp and 98

---

### Post by jualin on 2008-08-18
If the XP boot loader has the Windows 98 partition then one entry for XP in the Grub should be enough. If you don't want to go through the hassle of setting up Grub manually, download a copy of [Super Grub Disk]("wwww.supergrubdisk.org") and it will install Grub automatically. Hope this helps!

---

### Post by Whydoe on 2008-08-18
Awesome.  Thanks.  I think my son will be the only kid going into grade 2 with the use of linux and 2 other os's.

---

### Post by jualin on 2008-08-18
> **Whydoe said:**
> Awesome.  Thanks.  I think my son will be the only kid going into grade 2 with the use of linux and 2 other os's.

I wish I had that opportunity when I was a kid, :).

---

### Post by Whydoe on 2008-08-18
Ya, I was "stuck" with a Commodore Vic-20.

---

### Post by jualin on 2008-08-18
I was stuck with no computer. The beauty of living in Cuba, :lol:

---

### Post by marine63 on 2008-08-19
i think your kid will be the only one who ever used windows 98 o.O
if you can get a copy of system shock 2 for your kid (its for windows 98) do it! its one of the best games ever made... though you might wanna wait a few years since the game is kinda scary O_O

---

### Post by Whydoe on 2008-08-25
I think I have that game.  :)  Anyway, NEW PROBLEM.  I've taken my sons currant Win98 hard drive and put it in the newer computer.  Then installed XP on the other hard drive so that both O/S's dual boot.  Then I went to take the 3rd hard drive and clone my Ubuntu install from my computer.  That's when the problem start.  The first hard drive I tried had bad sectors (or so I think) as it returned an I/O error during the dd command.  No problem... took another hard drive and tried again.  However, this time the destination hard drive was smaller than the original - even though the data on the Ubuntu drive would've fit.  Didn't realize you can't use dd to move a large partition to a small one.  So, I tried to fix the other hard drive and recover my bad sectors.  That seemed to work, and I went about reconnecting the hard drive to my computer to clone Ubuntu again.  However, now Ubuntu boots into Busybox.  Would a faulty hard drive on one of the partitions (even though it is relatively blank) cause Ubuntu to be confused?  I originally formated the hard drive (Ext3 with Linux Swap) and it worked fine.... but after the bad sector errors Ubuntu seems to reject the hard drive.  Any suggestions?  Perhaps re-formating the hard drive?  My computer boots fine once I re-attach my original hard drive (which is just an NTFS data drive).  Thanks.

---

