---
title: "Reïnstalling PC - dualboot XP/DD - partitioning questions"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by Thardus on 2006-10-03
My current system holds 2 internal HDD's:
- 1x 80GB ATA
- 1x 160GB S-ATA

Currently the 80GB holds my Vista RC1 install (20GB) a 10GB documents partition ("My Documents") and everything else is shared workspace (vFAT)
My Ubuntu disk is the 160GB one, currently holding the /, /boot, /home and some other junk partitions.

I'm not happy with the layout of the disks, as I lose way too much space for the /home partition for example and I didn't think about sharing my documents partition.

So I'm thinking about this partition setup:
```
___ 160GB	- MAIN
- 00.25GB		PRI	boot	EXT3	/boot		_bootloader space
- 20GB		PRI	XP	NTFS	C:		_system & programs
- 20GB		PRI	Linux root	EXT3	/		_root partition
- 40GB		EXT	XP Games	NTFS	D:		_xp games
- 30GB		EXT	linux home	EXT3	/home		_home partitioin
- 49,75GB		EXT	workspace	NTFS	E:		_workfolder for programs (e.g. DV stuff)

___ 80GB	- SHARED FILES
- 20GB		PRI	SHARED	vFAT	F: & /docs		_"My Documents" -including shared mail
- 60GB		PRI	MEDIA	vFAT	G: & /media	_MP3/movies/podcasts/downloads...

EXTERNAL 120GB
currently full NTFS containing backups ...
```Does this seem like a good partition scheme? Also, the partition types (EXT, NTFS, ...) are they a good choice? Isn't ReiserFS sometimes better? vFAT is needed for the shared partitions, I doubt there is an alternative for them. Furthermore, are the sizes OK? Other remarks you think of?

---

