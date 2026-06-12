---
title: "Found solution to problem with WindowsXP install after Gutsy"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by crunchfighter on 2007-12-21
I had a new hard drive and loaded it with Gutsy first.  I decided to set it up for dual boot but only have IBM recovery CDs and not normal windows install CDs.  I had Gutsy up and running, and with no prep of the drive, I put in the recover CDs assuming it would format the entire drive...not so...

After install of Windows XP, on reboot the GRUB fired up and gave me "error 22".  What was GRUB still doing here?  It should have been formatted.  I repeated the effort...(another hour) and same problem.

I pulled out an old copy of Norton Ghost and fired it up with that expecting it would have a format c: tool, but not so.  However, it did have an option to "reassign the Master Boot Record" or something to that effect.  Even though it showed the c: drive as the MBR, I reselected it.  I also redesignated the only displayed drive as the primary drive.

I rebooted and Windows fired up!  Now the machine is busily installing AOL, TaxCut, a whole bunch of proprietary IBM cr@p that I will have to remove, but I am on my way to a dual boot.

I hadn't read this anywhere, so I figured maybe someone else could use it.  I suppose there is a way to do it with the Gutsy LiveCD, but I don't know how.

---

### Post by Partyboi2 on 2007-12-21
A good troubleshooting page for grub errors is Hermans grub page. Its a handy page to have bookmarked.
[http://www.users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors](http://www.users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors)

---

