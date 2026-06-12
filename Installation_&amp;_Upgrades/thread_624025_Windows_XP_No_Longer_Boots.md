---
title: "Windows XP No Longer Boots"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by ostrowlaw on 2007-11-26
Hi,

I installed a disk version of Ubuntu 7.2 on my computer.  After installation, Windows XP would no longer boot.  If I selected Windows from the opening Grub menu, the windows logo shows up, and then the computer reboots.  Again and again....

So, I went into the Windows XP disk and reinstalled the boot sector -- no luck.  Then, I uninstalled Ubuntu (deleted the partition) and used my Windows 98 disk for format /mbr

Still no luck.  The Ubuntu seemed to mess up the boot sector.

Reinstalled Linux (this time using Suse Linux 10.2).  Again, Grub sees the Windows partition but it cannot boot.  I have all of the Windows files (thankfully, all my photos, etc are still there) but I cannot boot into Windows.

Anyone have a clue here?

Thanks.
Alan

---

### Post by tinycamp on 2007-11-28
first, try to recover your windoze boot sector booting with the win install disk, using rescue mode

look for a command fixboot or fixmbr.... dont remember

good luck!

BACKUP YOUR STUFF ASAP

---

