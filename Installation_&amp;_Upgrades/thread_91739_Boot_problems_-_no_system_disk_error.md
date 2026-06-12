---
title: "Boot problems - no system disk error"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by psyguy92 on 2005-11-17
Oh the pain...

I was using a desktop PC with a triple boot (Ubuntu, Fedora Core 4, WinXP), and got a new computer, so I gave that one away.  As I knew the person would never use Ubuntu/FC4, I used Partition Magic under windows to delete the linux partitions and merge the freespace into the WinXP partition - the only remaining partition.

Ok, so I'd written GRUB to the MBR, and after removing the Linux partitions, the computer wouldn't boot.  I used an XP recovery disk from bootdisk.com to do a FIXMBR or fdisk /MBR (forgot which one worked), and that fixed windows - no problem.  Then a couple of weeks later I start getting a non system disk error when booting.  Cold reboot usually fixes this.  I thought maybe the rigging of the MBR was a problem, so i reinstalled Ubuntu in order to have GRUB on the MBR again, defaulting to XP to load.  I still have 'no system disk' errors at random when booting, and need to cold reboot.  At times, the computer will even turn off during operation under XP now, giving that same error.  It's virus/spyware free, btw.

Does anyone have any ideas on this ?  Would a complete format and reinstall of XP be in order here?  Also, the XP disc for that install is no more.  I only have a Dell XP disc, and I'm not sure it is a straight XP and not restricted to the laptop.  In hindsight, I should have left the Linux partitions in tact.  Does this sound hardware related, or partition/OS related to you guys?  What would cause this??
:confused:

---

