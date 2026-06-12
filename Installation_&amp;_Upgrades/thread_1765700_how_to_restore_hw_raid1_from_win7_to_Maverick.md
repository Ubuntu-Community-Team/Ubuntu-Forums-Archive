---
title: "how to restore hw raid1 from win7 to Maverick"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by speed32219 on 2011-05-23
During installation of 10.10 I used clonzilla to backup the 10gb OS partition to **/dev/sdb1**.  What I meant to do was backup the root partition to **/dev/sdd1**!

Fubar'd,damn, &%$*ing idiot!  OK, so I deleted the partition and but the ntfs file system back on.  I thought during boot the system would see a new drive same size and re-sync.  Nope, just gives me a freaking error and then loads.

stuff:
/dev/sda - 60 GB (10GB /Root, 4 GB swap and the rest to /home)
/dev/sdb1 - data 566GB (2tb drive)
/dev/sdc1 - data drive that **needs to re-sync **0GB data (2tb drive)

The manual for asus M4A88TD-M does not give instructions on how to recover.  It states that the raid is OS independent, but I need to create another raid disk driver with usb or floppy using Windows!  

Anyone know what I can do to get the hw raid1 working again?

What I don't understand is, if I have a disk failure and replace the disk (which I essentially did) isn't the raid suppose to re-sync automatically?

---

