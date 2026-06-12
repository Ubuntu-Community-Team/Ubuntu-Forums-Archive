---
title: "SSD RAID TRIM AHCI drives partitions options and probably debate"
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by SirWeazel on 2014-10-22
I can see this topic branching off into a debate, and i'm open to all options and opinions. My questions arise from the hardware i have, the options this provides, and the multiple views to approach this issue. I've tried to research this myself with conflicting data/results. This is probably because this tech is more common and changing so quickly.   Let me thank you in advance for your input....

Hardware:
I have a MSI GT70 laptop  with a 750GB 7200RPM hard drive and 256GB SSD super raid. Super Raid is confusing, so to simplify I really have 2 128GB SSD drives and 1 750GB Drive. If you need more specs i can provide additional info.

My original idea was hardware raid 0 the 2 128GB drives into 1 256GB drive and install the OS onto this, but then i was worried trim would not pass through to the raid setup. If trim does work, this would probably be my option.

Currently i have the OS installed on 1 SSD, /HOME mounted on the other SSD. The spinning drive is for data, pictures, videos, virtual machines, ect...  But this is alot of wasted SSD space since i've never had / root take up a lot of space.

I've also thought about LVM, but i'm not super familiar with this and i'm also worried about trim support.

I think i would really like to combine the 2 SSD drives into 1 drive.  What do you think?
I will be using several VM's, games, steam games, and various activities.

---

### Post by oldfred on 2014-10-22
I prefer reliability and ease of configuration.
And I install Ubuntu to every hard drive. Even if just another working test install or another way to boot.

So I would not suggest RAID 0, nor LVM, but others do like either or maybe both who want lots of speed.

I might keep /home on SSD and only have on hard drive data partition for larger files like videos and a backup of SSD data. You still should have other backups so if you delete or modify a file you have the older copy somewhere.

Not sure about trim issues. I have converted from discard to using a cron task with fstrim.
 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

      
 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

I think LVM disadvantages outweigh advantages, but this is from a user who likes LVM.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

