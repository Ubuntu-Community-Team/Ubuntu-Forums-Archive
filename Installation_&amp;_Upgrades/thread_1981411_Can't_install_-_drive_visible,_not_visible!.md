---
title: "Can't install - drive visible, not visible!"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by olly11 on 2012-05-16
Hi folks, ok so I have an older computer that had Ubuntu 10 installed until the hard drive died last week. Replaced hard drive with an old IDE 40gb unit that is spare, and confirmed ok with XP.
I load the Ubuntu cd, in this case V12. Test everything out with the trial mode, view the hard drive, which I think is visible as 40gb storage or something similar.
Now the trouble is, when I select to permanently install Ubuntu, I get as far as the partition selection screen and nothing appears in the list, so I can not continue with the install! 

When I select next, I get an error suggesting I select a partition (I think), and then I see some text showing the system scanning, and finding a drive / partition, but again nothing appears, and non of the buttons work, although I guess because I have nothing to select in the list!

Tried reformatting the drive in both NTFS and FAT32, with no difference. Made sure the drive is master, no problems. There are no settings in the bios that can be changed apart from mode, this has always been set to auto.

So for some reason, while Ubuntu is capable of seeing the drive, it is not recognizing it as a valid installation medium!

I have tried v10, 11 and the latest 12 with the same error!

Can anyone point me in the right direction please..?

---

### Post by darkod on 2012-05-16
Is it possible it was used in RAID earlier? In that case you need to remove the raid meta data from live mode, in terminal, with:
sudo dmraid -E -r /dev/sda

If that asks you if you want to remove the meta data, this was the issue. Confirm and it should be fine.

---

### Post by efflandt on 2012-05-16
Boot an install CD (or bootable install iso on USB) to a live system and see what gparted there shows for the drive, especially **!** warning.  If gparted thinks there is something wrong with a Windows partition it will not allow you to modify it and will recommend fixing it from Windows.

And post the output of **sudo fdisk -l** (small L), but wrap that in code tags by highlighting it and clicking **#** in message window here to wrap it in code tags to preserve formatting (columns).  That may reveal type of partition(s) and if they are in the proper order.  Linux should have no problem with normal msdos partitions (fat or ntfs), but cannot work with Windows proprietary volumes.

---

### Post by olly11 on 2012-05-17
Thanks folks, seems darkod hit the nail on the head :) Brilliant!

---

