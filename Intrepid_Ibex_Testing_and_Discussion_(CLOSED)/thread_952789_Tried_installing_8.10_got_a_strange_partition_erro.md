---
title: "Tried installing 8.10 got a strange partition error on boot"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jordan777 on 2008-10-19
I know it's beta but I'm getting some weird errors when I try to install it.  I'm using the live cd right now as my computer won't boot windows any more.  I installed 8.10 and when I rebooted I tried to run it but it said there was a partition error or that it isn't recognized or something like that.  That's pretty strange...  It says something similar for windows.  I think if I just delete the partitions I added (which includes grub in there) that I could at least go back to using windows but I want to use Intrepid.  I don't think it would be because I'm trying to use the 64 bit version.  I have an AMD64 X2 5200+ and 2GB of ram so that should be ok.  Maybe I just partitioned wrong or something?  

This is how I set up my partitions
NTFS - 130GB
/ (ext3)- 12GB
SWAP- 2GB
/home (ext3)- rest (~160GB or so)

Anybody have any suggestions?

---

### Post by caljohnsmith on 2008-10-19
So do you get a Grub error on start up at all? How about posting:
```
sudo fdisk -lu
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
Replace "sda" above with whichever HDDs you have, and then for each HDD that returns "GRUB", replace <drive> with that drive and post the output of:
```
sudo dd if=/dev/[COLOR="Red"]<drive>[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
Also, for whichever is your Intrepid partition, please post the output of:
```
sudo dumpe2fs /dev/sdX | grep -i "inode size"
```
And replace sdX with your Intrepid partition.

---

### Post by Jordan777 on 2008-10-19
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001d285

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbec3bec3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   286712054   143355996    7  HPFS/NTFS


This was the output of the second code you gave me.  I don't exactly understand it because it shows... Aw crud I forgot I deleted my intrepid partitions from the 320GB hdd.  I want to try and partition and install it again but it'll probably just give me the same error.  I reinstalled once before already and I just got the same thing.  Maybe I'm just doing something wrong during the partitioning phase?

---

