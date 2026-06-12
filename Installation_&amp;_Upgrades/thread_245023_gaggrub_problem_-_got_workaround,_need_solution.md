---
title: "gag/grub problem - got workaround, need solution"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by siman on 2006-08-27
hi guys,
I have a dual-boot system XP, dapper - it works pretty well, but without me interfering GAG (gag.sourceforge.net) sometimes tells me "boot sector can not be found", when I select to boot XP or ubuntu (both!!). This behaviour is strange, and it seems this only happens when my computer is off for a couple of hours. I can reboot like stupid, and GAG will always find the "boot sector", but once I leave the computer off over night I can be sure, that in the morning it won't find them anymore... I know this sounds crazy.

I know how to fix it, though: I boot up the alternate CD and reinstall grub into /dev/hda1 and after that GAG finds the ubuntu AND the XP "boot sector" :-)

my partition table looks like this:

```

/dev/hda1 - ext3
/dev/hda2 - winxp NTFS

/dev/hdc1 - root ext3
/dev/hdc2 - home ext3

/dev/hdd1 - ext3

```

I have GAG installed on /dev/hda. When I install Gag, it finds XP "bootsector" on /dev/hda2 and ubuntu's on /dev/hdc1.

I have to admin that the boot sectors of all HDs are a bit messed up, for example on /dev/hdd1 there are entries about an old ubuntu  installation and stuff.

---

Do you see any reason, why GAG might not be able to find the boot sectors? This is always so easily fixed with the alternatecd-reinstall-grub stuff, but fixing this once and forever would be nice.

thx & bye
 simon

---

### Post by siman on 2006-10-06
as a follow up: I'm pretty sure the HD on which I had the first bootloader was corrupt. withouth this HD everything works good.

---

