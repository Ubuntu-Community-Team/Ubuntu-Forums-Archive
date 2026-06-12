---
title: "help!"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by ninjip on 2008-08-28
well ubuntu isn't really the OS for me. so I bought a new windows XP CD but when I try to install it it always says there are missing hardrives and stuff. Is this due to my ubuntu installation? or is it a problem with my computer itself??!

(really needa fix this quick)

---

### Post by qwerty6523 on 2008-08-28
why isnt ubuntu the os for you

---

### Post by kellemes on 2008-08-28
> **ninjip said:**
> well ubuntu isn't really the OS for me. so I bought a new windows XP CD but when I try to install it it always says there are missing hardrives and stuff. Is this due to my ubuntu installation? or is it a problem with my computer itself??!

(really needa fix this quick)

Maybe you should clean your partitions using the Ubuntu LiveCD first, or something like [GParted Livecd]("http://gparted.sourceforge.net/livecd.php").
Windows is rather stupid with non native filesystems so maybe that's why it doesn't see your drives.

---

### Post by oilchangeguy on 2008-08-28
> **ninjip said:**
> well ubuntu isn't really the OS for me. so I bought a new windows XP CD but when I try to install it it always says there are missing hardrives and stuff. Is this due to my ubuntu installation? or is it a problem with my computer itself??!

(really needa fix this quick)

the fact the user has a non windows partiton has nothing to do with the windows cd seeing the hard drive. new hard drives don't come already formated ntfs people. the computer probably has a sata hard drive, which can sometimes give problems when trying to install xp.

---

### Post by ugm6hr on 2008-08-28
> **oilchangeguy said:**
> the fact the user has a non windows partiton has nothing to do with the windows cd seeing the hard drive. new hard drives don't come already formated ntfs people. the computer probably has a sata hard drive, which can sometimes give problems when trying to install xp.

I thought this too initially.

But I found that XP did not even recognise the presence of an ext3 formatted HD on an old desktop of mine, although wiping it with 0's using Active KillDisk made it visible.  So it appeared not so much that XP only recognises NTFS, but just doesn't recognise ext3.  Funny that after completing the installation, you can see the ext3 drive (As unformatted).

Very bizarre... And I have no rational explanation.

Nevertheless, I'd suggest wiping the HD with something like KillDisk, or just reformatting with GParted to vfat, and then formatting again with the XP install disc.

---

