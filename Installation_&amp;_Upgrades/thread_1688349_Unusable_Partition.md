---
title: "Unusable Partition"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by BillT506 on 2011-02-15
Hi, I'm installing Ubuntu on my latop as a dual-boot with Windows 7. I shrunk my C drive's volume by 20GB to use for Ubuntu, but when I boot from my CD and get to the stage where I choose the partition to use, the "Free Space" partition that I made is unusable. There's probably some super-easy way to fix this, but I'm completely new to this, so help would be very appreciated.

---

### Post by coffeecat on 2011-02-15
Almost certainly, the laptop manufacturer has set up 4 primary partitions, the maximum number allowed with a mbr partition table however much free space you have. It's not an HP, is it?

Boot up the live CD and choose 'try Ubuntu' to get to the live desktop. Post a screenshot of System > Administration > Gparted so that we can see the partition layout. You can use Print/SysReq to get a screenshot, or Alt+Print/SysReq for a shot of an active window. Or Applications > Accessories > Take Screenshot if the keyboard shortcuts don't work for you. Also, open a terminal (Applications > Accessories) and post the output of:

```
sudo fdisk -lu
```

They both say the same but in different ways but it will be useful to see both.

---

### Post by BillT506 on 2011-02-15
Yep, it's HP. Gonna do that now.

Okay, the Terminal command give me this:
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48764ce4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          409600   554328063   276959232    7  HPFS/NTFS
/dev/sda3       596271104   624928767    14328832    7  HPFS/NTFS
/dev/sda4       624928768   625140399      105816    c  W95 FAT32 (LBA)
Here's the screenshot:
[IMG]http://i52.tinypic.com/vh3ps5.png[/IMG]

---

### Post by coffeecat on 2011-02-15
Yes, I thought so: HP and four primary partitions - the maximum number possible. In case you don't know about the limitations of the mbr partition table (which is what you will have), a quick explanation. Primary partitions are numbered 1-4. If you need more than four partitions you can have one (but only one) extended partition instead of a primary partition. An extended partition is simply a type of primary whose sole purpose is to act as a container for a number of logical partitions. You can tell a logical partition in Linux from its number: 5 and upwards. Linux can boot from a logical partition; Windows cannot. For non-bootable partitions, for example data partitions, both Windows and Linux are happy with logical partitions.

The only way you will be able to install Ubuntu on that machine is to delete one of your 4 primary partitions and create an extended (and a number of logicals) in its place. Clearly, sda1 and sda2 are out of the question as they contain Windows. (In theory, you could move the Windows boot files from sda1 to sda2 and remove sda1, but there are better options.) Partition sda3 is your recovery partition for restoring Windows if you need to. That's a possibility for removal, but not necessarily a good one. Lastly there is sda4 which is your HP_TOOLS partition. I have no experience of HP laptops but I believe some owners delete the HP_TOOLS partition, having no use for the utilities in it.

Whichever partition you do decide to remove, I suggest you do two things first. Prepare some recovery DVDs with whatever utility HP has provided. These should be able to be used as an alternative to the recovery partition. I'm assuming here that HP provides such a utility since every other reputable manufacturer does. The other thing is to make images of all your partitions with a Windows imaging software such as Acronis True image or Norton Ghost. If you have neither, I can recommend Macrium Reflect which is free to download and use:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

I strongly urge you to do all that. I have seen more threads on this forum than I care to think about where people had lost Windows one way or another and did not have the foresight to create restore DVDs or backup images. It is so easily done.

Having done all that and when you have decided which partition you want to remove, you might find this link useful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Quackers on 2011-02-15
And, if you haven't got one already, make a Windows repair disc.
In Windows go to Control Panel > Backup & Restore Centre then in the left pane click on "make a recovery cd" - note that this is not a recovery dvd, but a repair cd. It may be worth its weight in gold :-)

---

### Post by coffeecat on 2011-02-15
> **Quackers said:**
> And, if you haven't got one already, make a Windows repair disc.

Good thinking, Quackman! :p I heartily concur. I hope the OP has plenty of blank discs.

---

