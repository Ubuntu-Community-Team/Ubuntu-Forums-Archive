---
title: "Installing to a laptop with a hybrid drive"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by tallperson on 2012-08-01
Hi

I have the task if installing 12.04 to a new laptop with a Hybrid Drive. It's a 32GB Samsung SSD with a 500GB Hitachi HDD - a Dell Inspiron 14z. It appears the two disks are in a software RAID setup.

The normal graphical Live CD installation does not show any partitions (due to RAID I think) but the alternate ISO does and prompts me to remove or keep the RAID setup.

I've got to the point where I need to partition the system and I'm considering doing a manual partition.
My goal is to install the OS to the SSD and have the 500GB drive as data (/home)

Can anyone provide any pointers on how this would be set up using manual or guided partitioning ?

I don't want to end up with a bricked system and I'm concerned there is "feature" in the BIOS that won't like this setup.

Thanks!

---

### Post by mhasoba on 2012-08-01
Hi,

I have precise-ly this question! I have a Dell XPS 14z with a 32GB ATA Samsung SSD + 500 GB Hitachi ATA HD. I had a go at installing Precise (64 bit) on the SSD and then manually auto-mounting the 500GB HD, with mixed results. I am hoping a more seamless solution exists. 

Thanks,

Samraat

---

### Post by darkod on 2012-08-01
It's not a software raid, from what I have seen mentioned here it seems it's some sort of raid0 fakeraid, the two disks together in continuous space although real raid0 should be from equal disks. The Alternate CD is asking you whether you want to activate the fakeraid array.

If you don't care about windows that might have been delivered with it, people have been able to "split" the disks by deleting the raid meta data with:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

Note that those commands might break the windows install, not sure if it will work after that. But I think 100% the disks will show as separate after that.

Not sure what you can do if you do want to keep windows.

EDIT PS: You also might need to enter BIOS and change the SATA mode from RAID to AHCI before that.

---

### Post by oldfred on 2012-08-01
Darko's instructions are what this thread ended up doing as near as I can tell. You end up not having the Intel Smart Reponse but then have a SSD & hard drive without the RAID.

 Intel Smart Response Technology.
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2033279&highlight=smart](http://ubuntuforums.org/showthread.php?t=2033279&highlight=smart)

---

### Post by tallperson on 2012-08-03
Thanks for the info and links, this worked very well.

I manually partitioned the disk after reading about and running dmraid commands.

the 500GB HDD (/dev/sda) gets /boot, swap and /home
the 32GB SSD (/dev/sdb) gets / with grub installed to this.

The laptop boots in about 10 seconds, compared to 1 minute on a fresh Win7 install and turning off all the hmm "add-ons" on a new Windows.

Thanks again.

> **darkod said:**
> It's not a software raid, 

---

### Post by Baladya on 2012-10-16
> **tallperson said:**
> Thanks for the info and links, this worked very well.

I manually partitioned the disk after reading about and running dmraid commands.

the 500GB HDD (/dev/sda) gets /boot, swap and /home
the 32GB SSD (/dev/sdb) gets / with grub installed to this.

The laptop boots in about 10 seconds, compared to 1 minute on a fresh Win7 install and turning off all the hmm "add-ons" on a new Windows.

Thanks again.


Hey Tall Person... I wonder how did you install / to the SSD... In GParted it says the SSD is divided into 2 partitions (8 GB and 22 GB). The 22 GB is used by Windows for the IRST. So did you install Linux on the 8 GB or did u extend the partition or what?

---

