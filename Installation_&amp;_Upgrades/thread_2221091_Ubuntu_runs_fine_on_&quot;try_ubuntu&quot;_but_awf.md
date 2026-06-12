---
title: "Ubuntu runs fine on &quot;try ubuntu&quot; but awful once fully installed."
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by Bridger_B on 2014-04-30
Hello, I am looking to install ubuntu on a 16GB flash drive. I can try it on my 4GB flash drive. But every time I install it the 16 everything runs very poorly. I have tried 3 times installing from the 4GB.

---

### Post by sudodus on 2014-04-30
Welcome to the Ubuntu Forums :-)

There can be different reasons why it runs poorly after installing.

1. Hardware in the computer

Some hardware driver that was available in the live session is not installed. You must tell us the specs of the computer to get more detailed tips about this alternative.

computer brand name and model
CPU
graphics chip/card
wifi chip/card

2. The method to run the pendrive, and the hardware in the pendrive (the flash memory)

a. The live session reads the compressed file system and expands it into RAM, and the live system will be quite responsive.
b. A persistent live session will be slower, because it must read the overlayed modifications from the casper-rw file or partition.
c. An installed system will be slower, because it must read the system directly from the pendrive.

b. and c. will be slower than a. for regular USB pendrives, but if you get a fast USB 3 pendrive, it will work much better in the cases b. and c.

See this link (and the link from it concerning flash drive speed tests)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by oldfred on 2014-05-02
You also want to minimize writes.
Linux systems also have journal which are good for recovering corrupted data, but slow system down and update file access times.  

So use ext4 but turn journal off. fsck may take longer and you need to be careful to correctly unmount or shutdown before removing flash drive or it may be corrupted. And changing to not write access time update may cause issues with some apps.

       With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sdb1
sudo tune2fs -o discard /dev/sdb1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

 
If you really want journal:
This basically means that data may be written to the disk before the journal. Speed over safety see man tune2fs
tune2fs /dev/xxx -o journal_data_writeback

If you use Mutt.
realtime a reasonable alternative to noatime and works with some apps that need timestamps like mutt

And just using a lighter weight system so more fits into RAM and you use less disk access to flash drive also helps. If limited RAM use Lubuntu.

I find USB3 flash drives are faster even on my USB2 ports.

---

