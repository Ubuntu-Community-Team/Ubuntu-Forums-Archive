---
title: "Mirroring Hard Disk"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by craig.brisbane on 2011-01-05
I am using Ubuntu 10.10. I have a system set up with 1tb HD. I also have another 1tb HD which I'd like to use to mirror the other drive. so if the primary HD fails I can boot and operate from the mirrored drive. 

I've read that this is possible by using Raid. however I am confused if it is possible to set-up with a HD which is already set-up Ubuntu system. Also what what I can make out the mother board does not have a raid option.

Any suggestions for where to from here would be appreciated.

---

### Post by Fafler on 2011-01-05
I don't know how to move an existing installation to a RAID array and make it boot, but to get the data on a array, you can make a degraded RAID 1 array on the second drive, make a filesystem on it, copy all the data from the first drive, unmount it and add it to the array with the second drive. It will resync and you will have a working RAID 1 array.

Theres no reason to use onboard RAID. Linux software RAID is much better.

---

### Post by presence1960 on 2011-01-05
keep it simple! Use [clonezilla]("http://clonezilla.org/") to make an image of your disk or of your OS partitions and store the image(s) on the second disk. If anything ever happens you can restore your stuff by booting the clonezilla CD. If you want you can do what I did and eliminate the clonezilla CD by installing it on your hard disk. The instructions are on the clonezilla website. Once installed all it takes is an edit of the 40_custom file in GRUB to have clonezilla appear in the GRUB menu and boot right to it without a CD.

---

