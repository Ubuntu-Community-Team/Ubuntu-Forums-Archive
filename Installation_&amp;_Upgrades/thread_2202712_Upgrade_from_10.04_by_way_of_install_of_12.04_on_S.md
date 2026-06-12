---
title: "Upgrade from 10.04 by way of install of 12.04 on SSD, keeping data on HDD using bind"
date: 2014-01-30
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2014-01-30
When I installed 10.04 three years ago, I set up /home on it's own partition on the 1T HDD in this computer. I am now ready to upgrade to 12.04. I plan to do a clean install to a SSD, keeping the HDD with all the data now in /home in place.

When I run the live CD of 12.04, do I need to take care to do, or not do, something regarding the HDD, particularly in respect of /home, which is on (extended) partition sda5? For example, I believe that I do not need to format anything on the HDD, only the SSD. I wanted to include a screenshot here, but did not since it took way too much time to figure out how. [This needs to be a whole lot easier!]

Since there is no screenshot, here is a text rendition of the current HHD:
> unallocated 1Mb
sda1 swap  15Gb
sda2  /   (EXT4)  28Gb
sda3  Extended
sda5  /home  (EXT4) 467Gb
unallocated 1Mb
sda6       (EXT4) 423Gb

Because this will be a new install to a new SSD while retaining the HDD, things that occur to me that might need to be planned for:
1) Will the fact that the HDD still has swap and /, is this going to confuse 12.04 on the SSD
2) Similarly for /home on sda5, especially since I will be using "mount bind" to cause the folders in /Desktop on the HDD to appear in my /home/Desktop

I am planning to keep the same computer and just go to 12.04 so it is a BIOS rather than UEFI machine and therefore I will be keeping the extended partitions on the HDD.

(Everything above is as this [advancing] noob understands it, so please correct any errors).

---

### Post by ajgreeny on 2014-01-30
Just choose "Something Else" at the partitioning stage and you can set the new SSD to have a partition for root with mountpoint /, which you must set manually, and select to format the partition (I recommend ext4).  Your old /home partition will also need to be set as /home again by clicking on it and choosing Change (or maybe Edit; I can't remember), but do not select Format this time or you will lose everything.

Don't forget that you may find that the original disk device name has changed and is no longer sda, so you may need to bear that in mind when setting up partitions.

---

### Post by ubfan1 on 2014-01-30
Since you might be switching between 10.04 and 12.04, the desktops will be quite different, and the (hidden) files they write into your home directory will be different, maybe conflicting.  Consider just adding your old 10.04 home as a link or mount under your new 12.04 home to avoid possible conflicts.  The swap left on the hard disk is good, you really don't want swap on the SSD for wear reasons.

---

### Post by Odyssey1942 on 2014-01-30
> Consider just adding your old 10.04 home as a link or mount under your new 12.04 home to avoid possible conflicts Yes, thanks, that is what I plan to do. I will mount -bind the old /Desktop now existing on HDD to the new /Desktop on the SSD. It will then show up as if it were the new /Desktop. 

I am only just beginning to use this approach and still do not have a feel for what impact if any there will be on the hidden files in the old /Desktop caused by 12.04 on the SSD. My assumption is none, but that is more guess than knowledge based.

I will not be making a swap partition on the 120Gb SSD. I plan to use 25Gb for as /, and the remainder as an unmounted EXT4 partition for possible later use. Since most of my data will be on the HDD, I trust that 25Gb should be plenty.

My concern had to do with the existence of a system partition and a swap partition on the HDD and whether that might somehow cause complications in 12.04 on the SSD? I don't know what is going to happen in the grub boot, but am hoping 12.04 will see the HDD and dual boot the two systems.

---

