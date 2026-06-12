---
title: "XP sp3 Fat32 need an LBA flag from Gparted"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by mkham on 2010-11-24
This is a new bigger 160g laptop hard drive that I copied over the Win XP partition w Gparted from my 80g, 3 data partitions (from an external drive). The old one **has LBA flags on the XP partition and the Extended- should I turn them on on the new one- does XP or my bios want or need them, or can they cause any problems**???? I did make partitions with Gparted and other PM's on the old one, so maybe that turned on the flags (I didn't).

  When I tried this before, the new drive wouldn't boot without installing syslinux w SUPERGRUB boot disk, which may still be there, but then I accidentally trashed the C drive trying to add a GRUB menu with Supergrub (not knowing right arrow is ENTER).

Will installing Lucid Lynx 10.4.1 with GRUB2 find the Win XP and make the proper shortcut to it or should I fix the MBR w TestDisk or SUPERGRUB disk, if it doesn't boot?

I have a Acer Aspire 5003Wlmi Turion 64 ML32 1.8Gh, 1gig ram.  Do you recommend using the i386 or AMD64 version of LL? Any known problems with AMD64 Lucid Lynx 10.4.1 on this machine (now 4 years old)?
Thanks, all.

---

### Post by mkham on 2010-11-25
Thanks you wizards. Well to answer my question- first did it without flag after figuring out how to delete MountedDevices on already copied drive (Windows regedit can do it offline- cursor on LOCAL MACHINES, load hive in WINDOWS/SYSTEM32/CONFIG/SYSTEM). Only took 4 days of reading!! Worked OK. Then added LBA flag- OK. Booted up w no problems- syslinux still there I guess, but haven't installed Ubuntu. 10.4 and 10.10 seem to be pretty buggy, huh??????
Hope the new Grub2 cleanly overwrites the old.

LBA flag not important for Windows XP, have it on or not.

---

