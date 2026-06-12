---
title: "Lubuntu: Full HDD encryption upgrade from 160GB to 500GB"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by lp.descamps on 2015-06-06
Hi,

Anyone got experience with moving everything to another hdd?

i did this

Pre Req:

install new disk, install lubuntu using full disk encryption to get the structure.

Migration:

1. insert as usb the new disk and delete the vg (big mistake ... but learning ..)
2. fdisk -l | grep dev to find new disk. here i got /dev/sdb
3. pvcreate /dev/mapper/luks... -v . to create the physical volume
4. pvs . to check the new pv
5. vgextend lubuntu-vg /dev/mapper/luks... . to extend our current vg to new disk
6. vgs to check. so now we have both disk in the vg
7. pvmove /dev/mapper/luks… 
8. pvreduce lubuntu-vg /dev/mapper/luks...old
9. update fstab using blkid

it sort of works but very slow to boot up and shutdown down.

then i played around etc/cryptstab and update the uuid ... but now lubuntu boots up dont ask my passphrase and crash in emergency mode


any experience welcome :-)

---

### Post by TheFu on 2015-06-06
This is not a beginner level task.

There may be easier or different ways to accomplish this.

As for everything except the encryption, use normal backup/restore methods. Those still work just fine provided your backup methods are NOT image based.  Then do a fresh install to the new disk, and restore the settings, data, and HOME areas for users.  During the restore, you'll need to take care to NOT screw up the fstab, cryptab, and default/grub.conf settings which were setup during the installation with encryption.  I also use the --get-selections / --set-selections method to get all the previously installed packages back.  Should take less than an hour to restore the main OS and common data.  Large media collections will add restore time.

My backup/restore "fu" is strong, so I chose that method.

I keep all the PV, VG, LV stuff outside the backup/restore.  Then it becomes almost a file copy issue. Plus the new encryption will be "fresh" (whatever that means). 

It is probably easier to label all the partitions and use labels to mount rather than UUIDs too.

I just reread this and it may not make sense based on what you've posted.   Most of the LUKS + encryption + LVM how-tos I've found are 5 yrs out of date, so whatever you are doing, take careful notes and be certain you can get back to the initial state if something fails.

The biggest issue that I have is the live-boot Ubuntu's select/paste doesn't work. Don't know why that is - just that it doesn't work. Typing all that crap in is bad for my sanity.

---

