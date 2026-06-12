---
title: "and now windows won't boot...."
date: 2005-02-09
forum: Installation &amp; Upgrades
---

### Post by Professor Frink on 2005-02-09
Because it used to be the 4th partition and now it's the third (delete /boot root and swap from gentoo and now just root and swap for ubuntu).  I know i need to edit the boot.ini but it's NTFS, what should I do?
Does Ubuntu let me read/write NTFS?
Thanks,
Mike

---

### Post by Wim Sturkenboom on 2005-02-10
As far as I know, any Linux flavour still has a problem writing NTFS reliable. But I'm not sure.

Maybe [this Microsoft article](http://support.microsoft.com/default.aspx?scid=kb;en-us;119467) is of help.

---

### Post by crane on 2005-02-10
Are you saying that windows went from hda3 to hda 2?

You may be able to boot you XP disc and use it as a rescue disk. Just don't let it install/repair boot loader.
I wouls alo suggest making a linux boot disk before you start editing anything!!

---

### Post by thestarman on 2005-02-11
[QUOTE=Professor Frink]Because it used to be the 4th partition and now it's the third (delete /boot root and swap from gentoo and now just root and swap for ubuntu).  I know i need to edit the boot.ini but it's NTFS, what should I do?  Does Ubuntu let me read/write NTFS?  Thanks, Mike[/QUOTE]

Ah, Mike, your post seems to be missing a lot of info!  Have you already been doing multi (not just dual) booting?  Where is your NTFS boot partition located?  There's an important fact about that the Win 2k/XP/2003 BOOT.INI menu system that all should know:  Even though you'll find such a file in any of those OS partitions, the only one that controls which OS will be booted is the BOOT.INI file in the FIRST PARTITION OF THE FIRST HARD DRIVE!  Even if its only a small empty FAT16 partition.  Quite often it's a Win 9x FAT32 partition that had been installed before any Win 2k/XP/2003 OS.  So, what's in that partition??  If you deleted it and installed Ubuntu there, which I've seen some people do, then you made it impossible for any Win 2k/XP/2003 OS to boot up!  Blame MS for your present situation.

Daniel.

---

