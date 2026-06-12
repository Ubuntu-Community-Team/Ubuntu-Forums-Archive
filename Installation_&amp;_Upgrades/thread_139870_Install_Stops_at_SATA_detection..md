---
title: "Install Stops at SATA detection."
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by Boiler98 on 2006-03-05
I am trying to install Ubuntu on a Shuttle SN75 (discontinued now).  I tried installing Ubuntu a long time ago, but was unable to do so because of the same (I think) problem.

During the install boot my system stops at, or around, the following message:

[4294671.778000] ata1: SATA port has no device.
[4294671.778000] scsi0 : ata_piix
[4294671.932000] ata2: dev 0 ATA, max UDMA/133, 2401211728 sectors:
(blinking cursor)

Before I had my USB mouse plugged in my boot stopped at this point:
[4294674.138000] mice: PS/2 mouse device common for all mice

I first thought it was a mouse issue, but found there is still a problem with the SATA drives.

I put the drive on SATA1 and simply hung up the install 2 lines sooner.  The drive is in working order.  I have WinXP installed and am able to boot w/o trouble to that OS.

Help in the matter is appreciated!

---

### Post by andrewsawyer on 2006-03-05
Just a thought however if you have a raid controller built onto the motherboard, it may be worth disabling it.  I found that I couldn't install Ubuntu until I did this.

Let me know if this helps.

---

### Post by Boiler98 on 2006-03-05
I do believe SATA RAID is supported, but I do not believe I have it activated.  I've tried several settings to my SATA controllers, and one of the options is to treat the controler as an IDE or RAID - I've had IDE selected each time.

---

### Post by Boiler98 on 2006-03-08
A small bumbage, in hopes that someone might can suggest an alternate route.  Has anyone installed Ubuntu on a Shuttle SN75 or know where I should kick it so it will get unstuck? :)

---

