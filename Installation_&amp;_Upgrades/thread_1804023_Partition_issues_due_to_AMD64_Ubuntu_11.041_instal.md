---
title: "Partition issues due to AMD64 Ubuntu 11.041 installation"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by Gingerdan on 2011-07-14
Hi everyone

*it's meant to read 11.04, not 11.041.

I am still a little green with Ubuntu and need some advice die to an installation of Ubuntu 11.04 64-bit that repeatedly went **** up as the installation had issues with the "filesystem.squashfs". I have another laptop and the 32-bit Ubuntu installation had no issues.

Now got it working and noticed that I have 15 additional partitions, all of which taking up 6GB and have no data stored on them. 

I cannot work out how to return them to being Windows partitions, 90GB is a lot of dead storage space, and is essentially 20% of my HDD.

Thanks a lot in advance for any advice.

Dan

---

### Post by mikewhatever on 2011-07-14
Use Gparted from the Ubuntu live cd to delete the unneeded partitions, nothing else to it really.

---

### Post by Gingerdan on 2011-07-14
Hi Mikewhatever

I have googled all over the place but cannot find a solution. 

GParted shows the following but there is no way of removing the partitions without removing the highest number first. Does this mean that I should delete everything and reinstall again from scratch? Please find the GUI version below, the list is quite large and following the last on the below pic, there is /dev/sda/6, unallocated, /dev/sda/5, unallocated following.

[IMG]http://www.dwhitemusic.org/Screenshot.png[/IMG]

Thanks a lot for your advice.

Dan

---

### Post by Quackers on 2011-07-14
It is not advisable to do it from a mounted system.
You should boot into the live cd/usb and select "try Ubuntu" then start gparted. You may then need to right-click on all the swap partitions and select "swapoff".
You should then be able to delete all the partitions you want to. 
If your Ubuntu partition is late in the disc that's fine. You can delete all the other partitions and leave just one swap partition (probably the one next to your Ubuntu root partition) then, if necessary reduce the size of your extended partition.
Then reboot and make sure everything still boots ok.
Then you can go into Windows Disk Management screen and extend your Windows partition to include the free space that you just created by shrinking the extended partition.
Take care not to increase the Windows partition past the beginning of the extended partition - big problems may occurr.

---

### Post by oldfred on 2011-07-14
You repeatedly installed side by side so the installer created new partitions each time you installed. After the first install did not work quite right you should use manual install (Something else in Natty) so you can choose the existing partitions that were already created.

You may just want to delete all the partitions as Quackers suggests with the liveCd. Then reinstall as your current / (root) is only 6GB. The 6GB may work but is small, I normally suggest 10-20GB as a minimum for root and then a separate /home for all your data for the rest of the space you are willing to allocate for Ubuntu.

---

### Post by mikewhatever on 2011-07-14
> **Gingerdan said:**
> Hi Mikewhatever

I have googled all over the place but cannot find a solution. 

GParted shows the following but there is no way of removing the partitions without removing the highest number first. Does this mean that I should delete everything and reinstall again from scratch? Please find the GUI version below, the list is quite large and following the last on the below pic, there is /dev/sda/6, unallocated, /dev/sda/5, unallocated following.


Thanks a lot for your advice.

Dan

You aren't using the live CD, which is probably why you can't delete the unneeded partitions. I don't think you should be deleting everything, but you have to use the CD.

---

### Post by Gingerdan on 2011-07-14
Found a "cheat" solution, thanks for all your help everyone.

I installed 10.04 and that worked a treat. Then booted into Win7 and manually deleted all the Linux partitions. Then, I booted off the Live CD and installed 10.04 again. 

Presto, all unnecessary partitions gone and already 10.04 seems more stable.

Cheers

Dan

---

### Post by Quackers on 2011-07-14
Lol :-), long-winded but successful nonetheless :-)
Well done!

---

