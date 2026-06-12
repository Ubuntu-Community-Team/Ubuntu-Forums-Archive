---
title: "NTLDR missing, installation a mess.."
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by android6011 on 2007-12-19
So this is what i did, i have 2 hard drives, a primary 160gb, and a secondary 40 gig. i had only gutsy installed, but i wanted to install hardy and xp (as a backup when hardy dies). I installed XP to my second hard drive first, it complained that it needed a windows filesystem on the first hard drive so i just deleted the first hard drives swap and XP installed to hdb fine. Then i installed hardy to hda, and grub did not add the XP partition on my second drive so I added 

title Windows
root (hd1,0)
savedefault
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)

and I get that NTLDR is missing. any suggestions? During the install Hardy deleted the partition windows put on the first drive so is it permanently broken?

---

### Post by logos34 on 2007-12-19
> **android6011 said:**
> ...and I get that NTLDR is missing. any suggestions? During the install Hardy deleted the partition windows put on the first drive so is it permanently broken?

It's not entirely clear to me what happened, but it sounds like windows specifically wrote the bootloader files to the partition deleted by hardy. I can't see how swap was the issue here.

That windows entry you added looks correct. 

Try this:

Go into the Bios **hard disk boot priority** (not to be confused with the device boot order) and set the slave/40 gb drive as first in the boot order. Then go back to the device boot order and set the cdrom first.  Boot the XP install cd and hit 'R' to enter the Recovery Console.  At the prompt run these two commands:

fixboot

and

fixmbr 

Hopefully it will repair the ntldr files and install the bootloader to the 40 gb drive's MBR.  Then remove the cd, reboot and go into the bios and change the hard disk boot order back to 1) linux drive and 2) xp drive, and let it boot to first hard disk.  See if that allows you to boot windows from grub.

If not, set the 40 gb drive back to first boot position in the bios and reinstall XP.  Then set it back to slave/second position and try once more to boot it with grub.

---

