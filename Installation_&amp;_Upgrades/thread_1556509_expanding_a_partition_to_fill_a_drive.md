---
title: "expanding a partition to fill a drive"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by AnalBeard on 2010-08-19
Ok, so I've recently (i.e. tonight) added a new drive to my raid and expanded the array to encompass the new drive. This migrated it from a raid1 to a raid5 (my card can handle online capacity expansion/raid level migration). Now the raid card's management cli shows the raid as being the new size so that went fine, but obviously I now need to sort things so debian can actually use it. My question is this: can debian expand an ext3 partition? Presumably, this would entail using fdisk? Ideally this should be non-destructive.

I've posted this here because I can't find anything particularly conclusive on google as to whether this is possible or not.

The server is running Lenny and it's gotta be cli-based.

Cheers in advance.

---

### Post by quixote on 2010-08-21
Is parted available in Lenny?  (The cli end of gparted.)  It will resize partitions, but I don't know if it's nondestructive.  Do "man parted" on your system and see what it says.

---

