---
title: "Flash Drive won't format"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by ki4jgt on 2009-11-27
I have a flash drive that will not allow me to change it's format type. In windows, it reads 7.9 gigs, but in Ubuntu 8.5 gigs. I've tried partitioning whatever is reformatting it, but when I plug it back in, it simply goes back to fat, the partitions are viewable, but reported as having no format. How do I get my drive to format to another format?

---

### Post by lemming465 on 2009-11-28
Can you post the output of running *sudo fdisk -lu* against the flash device (e.g. /dev/sdc)?

What's the make and model?  It might have some wacky vendor partition in front of the FAT partition windows is seeing.

If you ran something like```

sudo dd if=/dev/zero of=/dev/YOUR_USB_DEVICE_HERE bs=2048 count=100
```
it would probably wipe out enough of the stuff that you could make a brand new partition table containing whatever you want.  However, it would also destroy whatever partitions and data currently existed on the USB drive, and for some particularly brain-dead drives might even brick the drive.  See if there are any vendor limitations for your model before trying that.  

Just using *gparted* or fdisk or something to fiddle with the existing partition layout would be slightly less destructive.

---

