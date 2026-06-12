---
title: "Dual Booting: The Battle Plan"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by Virtute on 2006-10-08
Alright, so my goal is to make a dual boot between Win2k and Ubuntu.

Heres the situation:
Currently I have a hard drive that is 100% Ubuntu, and things have come up that require me to have a Win2k partition.  I have about 70 gigs of files which I absolutely have to keep through the process.


Things I cannot do:
-Buy a new hard drive and install Windows on it (no money)
-Resize partitions, install Windows and re-write the Windows bootloader afterwards with a new copy of GRUB so I can dual boot (knowing me I'd end up losing access to either partition one way or another)
-Put files elsewhere, perform fresh dual boot installation, put files back on computer (the biggest storage device I have is an iPod, which only has 30 gigs, 10 of which are already occupied by music)



So I came up with a plan.  Heres what I intend to do:
1. Use Ubuntu LiveCD to resize Ubuntu partition to 100 gigs (down from 200).
2. Format free space with ext3 and move 70 gigs worth of files over to it.
3. Delete old Ubuntu partition.
4. With the 100 gigs of now free space (from deleting the Ubuntu partition), install Win2k and then Ubuntu to make a dual boot on that partition.
5. Boot into Ubuntu and drag files from the storage partition created earlier back over.
6. Resize partitions as needed to fill up the drive.


Does anyone see any problems with this, and what should I be on the lookout for while doing it?

---

### Post by lugduweb on 2006-10-08
Resize sometimes works and sometimes don't...
I had both case with Dapper (but did a backup so it was ok for me).
If you really don't want/can't lose your file, I recommand you to find another way. If you can't buy a HD, maybe you can backup file on a friend's HD, perform a new install, then get back your files without any risk.

---

### Post by brickbat on 2006-10-08
Acronis Disk Director will resize perfectly every time.  It is lightning fast too.  Its not foss but it is best in class.

---

### Post by louistan3 on 2006-10-09
u could also backup using cd's/dvd's if you have a writer.. 
and i thnk you could jst leave the 100gb with the files and just make it ur /home partition.. after you install ubuntu.. instead of  returning it to the boot partition and resizing again.. :D

---

