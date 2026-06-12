---
title: "GRUB loading, please wait..."
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by daundeadrat on 2007-01-23
I'm trying to do a fresh install on my laptop, but it hangs on the screen showing
GRUB Loading1.5.
GRUB loading, please wait...

I'm installing it on my Alienware m5700 which uses 2 60g SCSI drives in RAID.  I read somewhere that if I disabled the raid in my bios it would help, but my bios doesn't have the option.  I've tried making the partitions on both hard-drives and the only difference I see is when installing on /dev/sdb, it will say "GRUB Loading1.5. GRUB loading, please wait... Error 22..." instead.  Any help would be greatly appreciated.

---

### Post by daundeadrat on 2007-01-24
/bump

---

### Post by daundeadrat on 2007-01-24
Ok, quick update:  By following another thread i've mounted the hard drive, checked my menu.lst file (all seems fine with it), and when I try to reinstall GRUB using  "sudo grub-install /dev/sda"  it gives me an error saying "Could not find device for /boot: Not found or not a block device"  Do I need to have a /boot partition, because I let Ubuntu do it's thing for the partitions and it appears it only made a / and /swap partition.

---

### Post by daundeadrat on 2007-01-24
Ok, another update, looks like I had the drive mounted to the media folder still and not /boot.  Once I ran grub-install it gave me a readout of the 3 drives it detected (fd0, hdo  /dev/sda, hd1  /dev/sdb) and the other thread said that might fix the problem...  no luck here. still stops at:  
GRUB Loading stage1.5.

GRUB loading, please wait...

---

### Post by daundeadrat on 2007-01-24
Fixed:  I found a hidden boot options menu in my bios for my harware RAID array setup and was able to delete the array.  Now all works fine.  Thanks for all the help...or lack thereof.

---

