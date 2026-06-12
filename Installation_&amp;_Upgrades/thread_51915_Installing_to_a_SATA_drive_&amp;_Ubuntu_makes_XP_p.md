---
title: "Installing to a SATA drive &amp; Ubuntu makes XP partition non-active and non-bootable"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by aveline on 2005-07-25
topic says it all ...

went to install ubuntu last night on a 60gb of free space partition I'd made with partition magic.  Everything seemed to go fine .. I made 3 partitions in the space (one / @ 20gb, 20gb /home & 1gb swap) making root (/) bootable.  It went thru stage 1 install, detected the SATA drive fine & rebooted...then I got "No bootable device or Insert device media and reboot to boot your device(s)"!!!  I paniced (sp?) and tried to reinstall xp thru their repair option, tried their FIXMBR and Fixboot utilities... nothing...Finally remembered abuot 3 am that it might have made all partitions non-active or something (had it happen before with mandrake...what a nightmare), so using the Ultimate Boot CD, I set the MBR to "active" again... xp booted and began reinstalling new system files.  ok great!... but I still do NOT have a working ubuntu & I'm almost afraid to try this again.
Btw I could NOT boot *any* cds while no partitions were active?!  not even live cd's..they stalled.  Ideas on what to do to get ubuntu installed?  And before someone says, use a floppy drive, I have none in this comp & I really don't wanna have to put one in b/c theres not alot of space inside to do it....plus tis a pita.

I have a workbench comp I was going to test this stuff on but right now, it won't boot any cd at all... tried making its partition active again but that didn't work this time.  Dunno if its the cdrom thats not booting cds properly or what just yet.  *sigh*

aveline

---

