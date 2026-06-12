---
title: "Kubuntu 9.10 on USB has only 500MB free space"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by elreteipos on 2010-02-12
I used Ubuntu's built-in tool to create a USB drive that boots into Kubuntu with persistence enabled. I said the tool could use 4.5GB of my pendrive, but now that I've booted into it I noticed only have 500MB to work with! How come? How do I fix it?

---

### Post by Cabs21 on 2010-02-12
did you put swap space on the drive?  Did it partition your drive smaller then 4.5 GB?  Is it a 4.5 GB drive or a larger drive partitioned into 4.5 GB?  Need answers and more info on what you are working with.  Also bear in mind that 4.5 GiB is only 4.18 GB.

---

### Post by elreteipos on 2010-02-12
All I know is that I used Ubuntu's built-in bootable USB creator, gave it the Kubuntu 9.10 ISO and said it could use 4.5GB to store its data in so that I don't lose my data when I shut down.

When I look at the total size of the hard drive, it says something along the lines of 500MB which is way less than I made room for.

---

### Post by C.S.Cameron on 2010-02-12
Have a look at the file named casper-rw, it is your persistence file. how big is it?
If you are booting from the pendrive you can find it in filesystem/cdrom

Also the file size limit for FAT32 is four gigs.

---

### Post by elreteipos on 2010-02-13
You bring up an interesting point. The drive is in fact a FAT32 filesystem, and the casper-rw file is nowhere to be found.

[img]http://img682.imageshack.us/img682/3763/filesl.jpg[/img]

Would you suggest converting it to NTFS or is that unsupported?

---

### Post by efflandt on 2010-02-13
How big is your USB flash or the FAT32 partition?  If you tried to set persistent file size larger than 4 GB (FAT32 filesize limit) maybe it did not create any persistent data.

Regular Ubuntu on 2 GB flash usually leaves room for up to 1 GB of persistent data (would fail if slider is all the way to 1.1 GB).  But I hear that the Kubuntu iso is larger.

Is that 500 MB you see remaining, a virtual filesystem, ramdisk, or remaining FAT32 space (which would not be used for persistent data, but could be used to store other files accessible to Windows, etc.)

---

### Post by elreteipos on 2010-02-13
[quote="efflandt"]How big is your USB flash or the FAT32 partition?[/quote]
About 8GB.
[quote="efflandt"]If you tried to set persistent file size larger than 4 GB (FAT32 filesize limit) maybe it did not create any persistent data.[/quote]
Turns out it didn't. I recreated casper-rw with a size of 3GB and that works fine.
Regular Ubuntu on 2 GB flash usually leaves room for up to 1 GB of persistent data (would fail if slider is all the way to 1.1 GB). But I hear that the Kubuntu iso is larger.

[quote="efflandt"]Is that 500 MB you see remaining, a virtual filesystem, ramdisk, or remaining FAT32 space (which would not be used for persistent data, but could be used to store other files accessible to Windows, etc.)[/quote]
I think that was a ramdisk, considering that I lost my data every time I rebooted.

Is it possible to route around this limitation by formatting my pendrive as NTFS partition or is this unsupported by portable Kubuntu?

---

### Post by C.S.Cameron on 2010-02-13
I have only been able to get usb-creator and unetbootin to work with FAT filesystems.
You can get more persistence by adding a ext2, ext3, or ext4 partition and naming it casper-rw, (if you want a separate home partition you can add another ext partition and name it home-rw).


This is what worked for me on a 4G flash drive.
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk".
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted the casper-rw file.
Shutdown, removed CD, rebooted.
Changed desktop background, connected to wireless and installed FontForge as an example.
Rebooted, changes were persistent.

---

