---
title: "Clone current Ubuntu 12.04 to install in new hdd"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by johnnydoe on 2012-05-07
I have been running Ubuntu 12.04 (not a live version) for a few weeks from a flash drive, while developing android applications.  I have made some modifications and would like to clone, or make an ISO, of my current system that is on the flash drive and put it on a SATA HDD.  I want to use the SATA as the primary working environment, so it needs to be bootable and all.

---

### Post by mips on 2012-05-07
You could try using something like dd or clonezilla to image the partition/drive and then afterwards resize it with gaparted to fit the drive.

Another option is something like Remastersys.
[http://ubuntuforums.org/showthread.php?t=1967865](http://ubuntuforums.org/showthread.php?t=1967865)
[http://ubuntuforums.org/showthread.php?t=1910591](http://ubuntuforums.org/showthread.php?t=1910591)

---

### Post by vVvSHADOWvVv on 2012-05-07
> **johnnydoe said:**
> I have been running Ubuntu 12.04 (not a live version) for a few weeks from a flash drive, while developing android applications.  I have made some modifications and would like to clone, or make an ISO, of my current system that is on the flash drive and put it on a SATA HDD.  I want to use the SATA as the primary working environment, so it needs to be bootable and all.

You should have run a VM to do this as I do not think it will ever run flawlessly by copying.

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by darkod on 2012-05-07
I don't like dd or clonezilla personally because dd copies empty space too (so you will wait longer), and clonezilla has the limitation of being able to restore only on a bigger partition, not smaller. In your case going from usb stick to a hdd that should be fine, but I still don't like the principle.

You can also use something like FS Archiver. That can restore to a partition smaller than the source, as long as the data fits.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

You will probably need to restore the bootloader and maybe touch few other settings after the restore. If you use clonezilla the UUID of the partition should stay the same I think, but with FSA the partition will keep its UUID which will not be the same as the one inside the ubuntu OS you are copying.

---

### Post by vVvSHADOWvVv on 2012-05-07
> **darkod said:**
> I don't like dd or clonezilla personally because dd copies empty space too (so you will wait longer), and clonezilla has the limitation of being able to restore only on a bigger partition, not smaller. In your case going from usb stick to a hdd that should be fine, but I still don't like the principle.

You can also use something like FS Archiver. That can restore to a partition smaller than the source, as long as the data fits.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

You will probably need to restore the bootloader and maybe touch few other settings after the restore. If you use clonezilla the UUID of the partition should stay the same I think, but with FSA the partition will keep its UUID which will not be the same as the one inside the ubuntu OS you are copying.


That's what I would be worried about is the UUID not meshing with the system on new hardware. I would have to read up on this to see how the UUID is assigned on new hardware. Good post darkod

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by oldfred on 2012-05-07
I am in the clean install and copy /home over family. Possibly some settings from /etc. If you have installed a lot of apps, you can export a list and reinstall. If you have not housecleaned the  downloaded .debs you can just copy & reinstall.

How ever you clone you have to edit/change UUIDs in fstab & reinstall grub to update its UUID references. There are at least a couple other files with drive info or UUID references and when an update to something happens it will want that UUID or drive.

If you try to boot with identical UUIDs, you may get updates to one system one day and the other the next and it gets confused.

Either way you have some effort to configure the new system.

---

### Post by ntu on 2012-05-11
In the past I have used the copy function in gparted, and clonezilla, to successfully clone one hdd containing my ubuntu installation to another hdd. Have also used partition wizard home edition (free)(installed to XP)for this.

---

