---
title: "Problem: Installer reporting ATA Drive (6.4 GB ATA ST36424A) as a SCSI device"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by NeedToKnow on 2008-09-14
Upfront details: 
	
Ubuntu version: 8.04.1 – Installing from LiveCD
Hardware: Compaq DeskPro EP series – 384 MB RAM – 6.4 GB ATA ST36424A drive – Blown away during initial install attempts

Sorry to be so verbose but I figured it best to get the details out there the first time so . . . 

Here’s the problem:

Installing using LiveCD, everything seems to go fairly well except for one small (and rather painful) detail. 

When the installer gets to the “Prepare disk space” section, my hard drive is being reported as a SCSI drive (/dev/sda). 

The two guided options don’t seem to report the drive correctly (as they call it a SCSI drive) however, the “Guided – use entire disk” option has a SCSI option but correctly identifies the drive as a 6.4 GB ATA ST36424A, which is correct.

When using the manual option to prepare the partitions the partition table is identified as /dev/sda.

If I create new partitions:

Type for the new partition: Primary
New Partition size in megabytes: 5998 – I’ve tried adjusting this with no effect – NOTE: Shows 1000 MB used
Location of new partition: Beginning 
Use as: Ext3 journaling file system
Mount point: / - I’ve tried changing this as well (/boot, etc.) – No effect

Once complete the drive is reported as:

Device: /dev/sda1

There are now 452 MB available as free space which I designate as a swap:

Type for the new partition: Primary
New Partition size in megabytes: 452 – I’ve tried adjusting this with no effect
NOTE: Shows 0 MB used
Location of new partition: Beginning 
Us as: swap

When the “Scanning disk” process is complete is reported as:

/dev/sda2 swap

OK, ready to drop the hammer and get going with the install, right?

Click on the Forward button . . . . the disk starts its thing and we move into the “Who are you stage”, fill in the details, click forward and get the Ready to install dialog.

Check the Advanced option:

Boot loader is selected – Device for boot loader: (hd0)

Click the install  . . .  and the system starts installing and gets to 15%, formats partition and then the good news . . . “The ext3 file system creation in partition # 1 of SCSI (0.0) (sda) fialed”

Click “OK”, go back to Prepare disk space and start jumping through the loop once more.

Boot loader is selected – Device for boot loader: adjusted to /dev/sda1 – Received Installer crashed message – Dead in the water!! Won’t boot from CD.

Any thoughts or suggestions would be helpful as it would now appear that I may need to simply restore to my previous OS.

Additional Info:

Disk info reported from GParted

Partition Editor: GParted

Device Information:

Model: ATA ST36424A
Size: 6.01 GB
Path: /dev/sda

Disk Label: msdos
Heads: 255
Sector/Track: 63
Cylinders: 784
Total Sectors: 12594960

Information about /dev/sad1

File System: ntfs
Size: 5.58 GB
Used: 3.47 GB
Unused: 2.12

Path: /dev/sda1
Status: Mounted on /isodevice

---

### Post by Pumalite on 2008-09-14
Get Gparted Live CD and clean your drive first. Delete everything in it. (unless you are dual booting). Then format. Then install.

---

### Post by NeedToKnow on 2008-09-14
WOW, that was fast &#8211; Thank you!

This sounds like a very good approach however, Live CD won&#8217;t boot (although others do on this PC), I&#8217;ve tried a slow burn to create the CD but, nope!

I&#8217;m going to try to burn the alternate to see if this works and take it from there.

Thanks again!

---

### Post by Pumalite on 2008-09-14
Try this one:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by NeedToKnow on 2008-09-14
Actually, I think you hit the nail on the head. The app I was using to burn the image didn&#8217;t appear to create a bootable CD although it would run the Live CD in an active OS.

I tried CDBurnXP and am now sitting at 40% of the system installed. I&#8217;ll reserve judgement until I reboot but, so far so good!

Thanks again!

---

### Post by Pumalite on 2008-09-15
Best is ImgBurn
Go to Mode>ISO>Burn
Select 1x as the speed of burn.

---

