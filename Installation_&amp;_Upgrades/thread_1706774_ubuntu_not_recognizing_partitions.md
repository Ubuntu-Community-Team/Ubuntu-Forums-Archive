---
title: "ubuntu not recognizing partitions"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by abu46 on 2011-03-14
hello guys 

i am trying to install ubuntu 10.10 on my system which has pre installed windows7 x64

i have 2x250 gb hdds
1 hdd has 2 partitions of 100 & 132gb while the other has no partitions

now when i boot through usb, ubuntu dosent recognize my partitions and considers it as a whole 500gb hdd (see screenshot) and i am not using any raid array or nvidia sw, infact i have an ati gpu!!

i want to install ubuntu on my first hdd by creating  a third partition of 12gb by creating ot using windows


also on which partition should i install the bootloader??

---

### Post by Kirboosy on 2011-03-14
Are you sure that you don't have RAID 0 setup? Because I've never seem Ubuntu automatically create a RAID array. 

To test this you could unplug the drive that Windows isn't installed on and see if your computer still boots. If it does then shut it down and plug the empty drive in and unplug the Windows drive.


~Caboose

---

### Post by abu46 on 2011-03-14
i did use an raid0 array on these pair of hdds long time back but since then i fully formated my primary hdd and also i have changed all my hw except hdds

its really strange that ubuntu is still seeing them in raid

is there any workaround for this except formatting the entire hdds?

---

### Post by Kirboosy on 2011-03-14
If you didn't physically break the RAID (going into the BIOS and shutting it off) then chances are its still in RAID. 

I guess you could use Clonezilla to make an image of the setup and re add it to the single HD after you completely remove RAID

Other than that you would have to wipe it out to fix it.

---

### Post by Rubi1200 on 2011-03-14
If you have no intention of using the drives in a RAID array and are sure you have backed up important data, you can safely remove the metadata and then try installing again.

Even if you format, RAID metadata can still be left over from previous usage.

From a LiveCD:
```
sudo dmraid -r -E /dev/sda
``` (or /dev/sdb, etc, depending on the disk name)

If it asks you to remove raid settings, that was the problem. Remove them and it should be fine.

---

### Post by abu46 on 2011-03-15
thnx guys :):)

problem solved

---

### Post by Rubi1200 on 2011-03-15
Excellent! Glad you got things sorted out :-)

---

### Post by Kirboosy on 2011-03-15
Awesome! Glad it was an semi-easy fix. :)

---

