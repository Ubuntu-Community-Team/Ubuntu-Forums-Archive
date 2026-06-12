---
title: "Computer won't boot into Ubuntu or anything else"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by wendell2 on 2015-01-13
I've tried just about everything. My Bios does recognize my new hard drive i just installed, it says "Hard Disk, Device verify failed". But when I booted up from Ubuntu live CD I was able to see the Hard Drive actually was working and being recognized so I installed Ubuntu to it, everything worked fine. But once I get to the point where it has to restart to finish the installation, this is where I run in to problems. When it notifies me to remove the Live CD and press Enter, once I press enter nothing happens, its like the computer is just freezes and I have to force the power off. I've also tried Boot Repair and I am still having the same problem. Here is my URL describing the problem: [http://paste.ubuntu.com/9730041](http://paste.ubuntu.com/9730041)

---

### Post by kansasnoob on 2015-01-13
> When it notifies me to remove the Live CD and press Enter, once I press enter nothing happens, its like the computer is just freezes and I have to force the power off.

What happens when you try to power back up without the live DVD? Are any errors displayed?

---

### Post by wendell2 on 2015-01-13
My BIOS recognizes the Hard Drive but it says "Device Verify Failed". Then it says "No boot device available - strike F1 to retry boot, F2 for setup utility"

---

### Post by fantab on 2015-01-13
From Live Ubuntu, open '**Disks**' and run SMART tests on your HDD, if tests fail then you have a bad HDD, if the HDD is 'healthy' then do as follows:

Check your BIOS for SATA mode, it should be **AHCI**.

Reformat your Hard disk, using [gparted]("http://Aidra Fox") from Live Ubuntu DVD/USB.
*Gparted -> Devices -> [create new parittion table]("http://www.dedoimedo.com/computers/gparted.html#mozTocId555890") -> choose default 'msdos' -> apply changes*.
You will loose all your data after this operation, so have a good backups of any data that you wish to save.

Then recreate partitions as suggested:
30gb Ubuntu '/' Primary ext4
4gb Swap Primary ext4
All remaining Gb Ubuntu /home Primary ext4

When installing Ubuntu use '**Something Else**' option from 'Installation Type' dialog.
Set up your '/' partition: Use As= Ext4; Mountpoint=/; format=yes
for /home Mountpoint=/home
Swap will be used, no need to do anything.

Tell us how it goes...

---

### Post by wendell2 on 2015-01-13
I figured out what the problem was. My hard drive had "PUIS" enabled so the drive wasn't visible during boot up so I loaded up HDAT2 from a CD and disabled "PUIS". It's was a 500GB hard drive I got out of my DVR, i guess DirecTV enables PUIS by default to save power. THANKS FOR THE THOUGH!!

---

