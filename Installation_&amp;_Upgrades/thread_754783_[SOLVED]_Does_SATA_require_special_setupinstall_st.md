---
title: "[SOLVED] Does SATA require special setup/install steps"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2008-04-14
New SATA WG2500YS.

I've never used SATA before. I installed the hard drive. No jumpers since the Western Digital site said that it should work without a jumper. It was a confusing set of instructions so I may have made a mistake.

It is an OEM drive and so has no jumpers or cd supplied.

I downloaded all the software but have not used any of it yet.

I ran the Ubuntu Live cd.

I opened a terminal and ran "sudo fdisk -lu". It just came back with a new prompt.

What do I need to get 'er going.

---

### Post by ubu-wan on 2008-04-14
I have done 2 installs to SATA drives without problems. Maybe you are thinking in terms of having to F6 install third party drivers on a WinXP installation; not the case with Ubuntu -- it just works!

HTH

ubu-wan

:guitar:

---

### Post by UBBU88 on 2008-04-14
yes.

It does work as is.  Windows xp stopped supporting the option from the install disc of supporting sata. Easy fix for that is download nlite. Iso the xp disc. download the sata driver for your board. slip it into the drivers section and install. 

That is, of course; if you want to have a dual booted system. And need to re-install xp. More than likely ubuntu sometimes corrupts the recovery partition for the xp system that came on the computer originally.


Just a pre-caution and a solution.

---

### Post by sofasurfer on 2008-04-15
But don't I have to onfigure my pc first?
In BIOS I have:

Under Integrated Peripherals I have Serial ATA Raid Configuration and NV SATA Controller.
I also am told to press F10 to enter the RAID Setup Utility. And I have no clue what to do with that.

---

### Post by UBBU88 on 2008-04-15
no dont worry abou thtat. basically once you have slipstreamed the disc. you wont have to worry about hitting f6. it should do it automatiicaly

tell you what? pm me with your mailing list, your computer type with model number, and email / msn, and we can chat further, so i can maybe just make you a disc quickly and mail it out.

---

### Post by Shazaam on 2008-04-16
I don't know about your motherboard but mine requires raid support to be turned on but NO raid array defined in the bios to be able to use SATA drives. Check the motherboard manufacturers website for info on your board.

---

