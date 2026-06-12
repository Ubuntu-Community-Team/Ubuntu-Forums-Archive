---
title: "Drive locations moved after motherboard change"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by Rob_Quads on 2007-06-05
I have just changed the motherboard of my system and its resulted in all the drives switching devices. Previously I had

```

Mothboard onboard IDE	Primary Master   =  80GB	/dev/hda
			Secondary Master = 120GB	/dev/hdc
IDE PCI Card		Primary Master   = 300GB	/dev/hdf	/md0 RAID5 array
			Primary Slave 	 = 300GB	/dev/hdg	/md0 RAID5 array
			Secondary Master = 300GB	/dev/hdh	/md0 RAID5 array
			Secondary Slave  = 300GB	/dev/hdi	/md0 RAID5 array
SATA PCI Card		1st 		 = 250GB	/dev/sda
			2nd		 = 250GB	/dev/sdb

```

After the change for some reason it screwed up the ordering of the disks, starting the devices at the PCI card rather than onboard

```

Mothboard onboard IDE	Primary Master   =  80GB	/dev/hde
			Secondary Master = 120GB	/dev/hdg
IDE PCI Card		Primary Master   = 300GB	/dev/hda	/md0 RAID5 array
			Primary Slave    = 300GB	/dev/hdb	/md0 RAID5 array
 			Secondary Master = 300GB	/dev/hdc	/md0 RAID5 array
			Secondary Slave  = 300GB	/dev/hdd	/md0 RAID5 array
SATA PCI Card		1st 		 = 250GB	/dev/sda
			2nd		 = 250GB	/dev/sdb


```

Anyone got any ideas how to get it to use the original drive lettering?

---

### Post by dabl on 2007-06-05
I'll venture to speculate that those designations come from the BIOS ID of the drives and their partitioning.  Probably you're going to have to manually change fstab and menu.lst to match the "new reality".

Two cents' worth (at most) ....

:)

---

### Post by Rob_Quads on 2007-06-05
The system works as I have the main drives working via labels so it has not actually broken the main setup but its extra things like hdparm setups which are configured from specific /dev/hdx drives. Also I am liable to do something silly prefering to the wrong drive

---

