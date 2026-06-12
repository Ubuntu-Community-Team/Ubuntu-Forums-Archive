---
title: "SATA Drive fresh install"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Exegete on 2007-11-27
I'm not new to Ubuntu, but don't post much.  I'm doing a fresh install on a Hitachi 80 gig SATA 300 drive. The Gutsy 7.10 CD doesn't see the drive.  Power and data cables are connected.  The drive list in the partitioning window is blank.

I've had Gutsy (and Feisty and Edgy and Dapper) running on the same machine, using an IDE 40 gig drive.  Processor is P4 2.8 gig, Motherboard is Biostar P4M80-M4, 512 meg DDR RAM.  The only change is the new SATA drive.

I tried booting off the old IDE drive with the SATA drive plugged in, but Gutsy didn't see the SATA drive then either.

Any suggestions?  I understand from reading similar threads that no SATA drivers are required in Gutsy.  Thanks in advance!

---

### Post by LeChacal on 2007-11-27
It sound like you problem is not with the OS or install disk but with you motherboard. Go into your BIOS and look for an option something like "SATA Emulation", the times I have had this problem I would change that option to "Separate IDE Controller". But I was booting from a SATA and using IDE as storage so you might need to try one of the other options if available. If you don't have that option my guess is still some option in the BIOS or a jumper/switch on the board that deals with the SATA controller on the board. That is my 2 cents.

---

### Post by Exegete on 2007-11-27
Thanks, LeChacal.  I'll poke around in the BIOS.

I don't know if it makes any difference to Gutsy, but my chipset is VIA VT8237R+

---

### Post by Exegete on 2007-11-27
BIOS appears to be set correctly - On chip SATA = enabled; SATA mode is set to IDE (not raid, I'm only using one drive).  There are no jumpers for this on motherboard.

If everyone is fairly confident that Gutsy should see a new, unformatted SATA drive, I'll go on the assumption that this is a hardware rather than a software problem.

BTW - I'm really getting used to Gutsy.  After I got the codecs and the DVD details worked out (using Totem), I don't see any reason at all to run Windows.  I am running Wine, with IE6, for those occasional sites that won't do Firefox.

---

### Post by Exegete on 2007-11-27
Problem solved.  The problem is the chipset - the VIA VT8732R has a known problem with SATA 300 devices.  There is a workaround on the VIA website, and a specific set of instructions for Gutsy - see [http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=143](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=143)

Thanks for the help, though.  I appreciate being steered towards a hardware issue.  You saved me a few hours of troubleshooting.

---

