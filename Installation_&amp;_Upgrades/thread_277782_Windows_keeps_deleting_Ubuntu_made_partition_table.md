---
title: "Windows keeps deleting Ubuntu made partition table"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by karlmdv on 2006-10-15
Hi All,

I've just installed a shiny new 160Gb Seageate IDE drive into a machine thats HDD just died.

I initially divided up the space like this:
hda1 80Gb  fat32  /media/windows
hda2 10Gb  ext3   /
hda3 59Gb  ext3   /home
hda4  1Gb  swap

I installed Ubuntu(Dapper Drake) and let it download the update packages rebooting afterwards (reboot was fine).  Then I proceeded with the Windows XP installation.  The XP disk is a pre-SP1 release.

When the windows installation got to the inspection of the hard disk it showed a single 'C' partition of 160Gb.  Sure enough when I rebooted at that point the machine wouldn't boot from the HDD and the Ubuntu installation showed the disk empty too.

I suspected that windows deleted the partitions because there was a FAT32 partition > 32Gb and so installed XP on the now empty disk in a 32Gb partition at the start of the disk (format, installation and reboot went smoothly).

Then I installed Ubuntu again setting up the partitions like this:
hda1 32Gb  fat32  /media/windows
hda2 20Gb  ext3   /
hda3 107Gb ext3   /home
hda4  1Gb  swap

The only thing I noticed that suggested something out of the ordinary was GParted displayed a "!" in a yellow triangle next to the FAT32 partition.  When I checked the partition information it showed a message:
"Warning: Unable to read the contents of this filesystem! Because of this some operations may be unavailable.  Did you install the correct plugin for this filesystem?"

Ubuntu installed smoothly but when I tried to boot into windows I got a near immediate BSOD.  The windows boot splash-screen didn't display and the BSOD message was completely generic, no mention of cause.

Hoping that I just needed to repair the partition table I used the XP install disk recovery console.  It wouldn't read the disk.  I rebooted and tried to do repair install of XP only to find that the installer was telling me there was a single 160Gb partition on the disk (sounds familiar).

I now suspect GParted is at fault here and have run it from the LiveCD console.

It spits the following message on startup (but otherwise appears to operate normally):
"Warning: Unable to open /dev/hdd read-write (Read-only file system).  /dev/hdd has been opened read-only.
Error: Unable to open /dev/hdd - Unrecognised disk label."

/dev/hdd is the DVDRW drive.

Any thoughts what's going on here?

---

### Post by richardhp on 2006-10-15
could try installing windows first, that way it thinks it's the boss and doesn't complain. Then when you install Ubuntu you can get GRUB to load before windows does, allowing you to choose between systems.

---

### Post by karlmdv on 2006-10-15
As I explained above, I tried installing windows first on the second try at installation.  Windows fails to boot after the Ubuntu installation with a BSOD.  GRUB installs and correctly detected the Windows installation when one was there.

---

