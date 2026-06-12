---
title: "How to set up dual boot with Kubuntu and Arch Linux"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by Annorax on 2012-08-12
I currently have Arch Linux installed and would like to install Kubuntu 12.04 as a dual boot. I see the "Prepare Partitions" section of the install but I am not sure what to do. I see the following:

/dev/sda
> /dev/sda1
> /dev/sda2
> /dev/sda3
> /dev/sda4

sda4 is my /home and I resized it to allow a new partition (ideally /dev/sda5), but via the installer it says the partition is "unusable" and gives me no option to format it or anything. What must I do to use it for the new install?

---

### Post by mwl128340 on 2012-08-12
it all depends on how it is partitoned now. the most primary partitions one can have is 4. you can create one extended partition and then have multiple logical partitions in the extended

---

### Post by Annorax on 2012-08-12
Via the Kubuntu Installer (or if there's a better way), how can I create an extended partition with logical partitions? It looks like these 4 partitions are primary.

---

### Post by LiamOS on 2012-08-12
I'd recommend tarring up your home partition, moving it to some external media and then removing the home partition, creating an extended partition in its place. In the extended partition, you can create multiple logical paritions; e.g. one for /home and then others for your kubuntu system. I'd also recommend having the /boot partition in common between them, and swap obviously.

If you'd like a more fully fitted partition editor, gparted is fantastic, and can easily resize, move and more.

---

### Post by mwl128340 on 2012-08-12
liam got it right. gparted is a powerful and great partitioning tool. if you got a live cd just throw it in and try kubuntu and gparted should be included.

---

### Post by mastablasta on 2012-08-12
> **mwl128340 said:**
> liam got it right. gparted is a powerful and great partitioning tool. if you got a live cd just throw it in and try kubuntu and gparted should be included.

gparted is not inlcuded in Kubuntu.

KDE partition manager on the other hand should be there.

---

### Post by oldfred on 2012-08-12
You may be able to convert your primary to an extended and then use gparted to modify sizes.

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

