---
title: "Dual boot Ubuntu on Vista"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by goonybird on 2012-03-06
I have successfully dual-booted with XP on a desktop [but since changed it to Ubuntu only]. When I set that up I started with a clean hard drive and had the XP disc.

My laptop came with Vista pre-installed and a recovery partition, so I have no Vista disc. How will this affect setting up a separate partition for Ubuntu?

Thanks

---

### Post by Bucky Ball on 2012-03-06
There should be a function to produce a series of Windows Recovery disks in Windows somewhere. If you do that (I generally do a couple of copies) you can then wipe the drive and install Ubuntu.

If you are wanting to install Ubuntu side-by-side with Windows;
* boot Vista, *shrink Vista with its own software*, **not** gparted, leaving free space to install Ubuntu to
* boot the Ubuntu install CD then choose 'Something Else' to manual partition when you get to the partitioning section of the install.
* Vista will be clearly visible on an NTFS partition. Don't go near it. Just make your Ubuntu partitions in the free space;

/ = root, where Ubuntu lives; 20Gb plenty
/home = where your personal data lives; large as you like
/swap = swap; 2Gb fine

... are advisable. Basically, it is absolutely no different from installing with XP. You can leave the recovery partition there or make the recovery disks and wipe it; whatever. ;)

---

### Post by Mark Phelps on 2012-03-06
> **goonybird said:**
> ... My laptop came with Vista pre-installed and a recovery partition, so I have no Vista disc. 

Even if you DID have disks, that is not a useful way to restore Vista.

Instead, after you get the Vista partition shrunk (using ONLY the Vista Disk Management utility), then you can make a restorable image by doing the following:
1) Download and install the FREE version of Macrium Reflect (MR) into Vista.
2) Image off the Vista OS partion using MR to an external drive
3) Use the MR option to create and burn a Linux Boot CD.

NOW, you have an easy way to restore Vista -- and with the added plus that you won't have to reinstall any apps, or lost any of your settings or data.

---

### Post by Bucky Ball on 2012-03-06
> **Mark Phelps said:**
> 
1) Download and install the FREE version of Macrium Reflect (MR) into Vista.
2) Image off the Vista OS partion using MR to an external drive
3) Use the MR option to create and burn a Linux Boot CD.



Interesting. Ta.

---

