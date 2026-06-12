---
title: "install freezefreezing during install"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by skream on 2008-06-04
I have an older system that i wanted to play with.

Celeron 600
64mb ram
10gig

Im trying to install xubuntu because i hear its good for low end systems.  I have tried several times to install and it stops at the same places every time. 

Partition drive?
??? ???
<yes> <no> 

basically after i hit yes it just sits at a blue screen.  If i hit CTRL+C it will end whatever process is running and go to the next screen which is "Setting up partitioner..." and it will get to 47% and stop every time.  At this point i have to turn off power to do anything.

---

### Post by quelx on 2008-06-04
Try the alternate CD 
[http://torrent.ubuntu.com/xubuntu/releases/hardy/release/alternate/](http://torrent.ubuntu.com/xubuntu/releases/hardy/release/alternate/)

or fluxbuntu
[http://fluxbuntu.org](http://fluxbuntu.org)

---

### Post by skream on 2008-06-04
im using the alternate cd, sorry should have mentioned that

---

### Post by Pumalite on 2008-06-04
Maybe you should try Damn Small Linux or Puppy.

---

### Post by wpshooter on 2008-06-04
Have you checked the integrity of your Xubuntu CD by running the verification function that is found on the initial Xubuntu boot screen menu ?

---

### Post by skream on 2008-06-04
> **wpshooter said:**
> Have you checked the integrity of your Xubuntu CD by running the verification function that is found on the initial Xubuntu boot screen menu ?

yes, cd checked good after i burned it and also in the disc integrity check

---

### Post by molotov00 on 2008-06-04
I had some wierd problems partitioning w/ the partinioner on the Ubuntu CD. I forget what the exact error was.

I got Ubuntu installed by using PartitionMagic, which I had installed on my Windows partition, and resizing the NTFS partition and leaving the rest as free space. I don't know your situation exactly.

I suggest partitioning (or at least freeing space) before running the installer.

---

### Post by steve.knoblock on 2008-08-10
I have the same problem with the desktop Hardy CD. I can reboot, select install from the menu and it goes okay until the partitioner screen opens. The progress bar goes to 46% and then stops with no partitions displayed and all the buttons grayed out.

I partitioned the drive with Windows XP when I installed it, so there is one big XP partition and a small one for Linux. There is no free space. The HD is SATA but the BIOS has the default mode as IDE so I don't think it is not finding the drive...but it may not be. When I start the desktop, I see no evidence it recognizes the Windows drive or any drive other than the DVD drive, which is IDE.

I defragged XP and restarted with the same results.

---

### Post by Pumalite on 2008-08-10
Assuming you have enough memory (384); try adding all_generic_ide at the end of your boot line.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by steve.knoblock on 2008-08-10
Adding

```
all_generic_ide
```

to the boot line (using F6 option) allowed the installer to find my 250 GB Sata HD with the XP and one free space partition. I was able to create (very tight squeeze into 8GB) root, swap and home partitions to at least get Ubuntu installed. I did not see a way to resize the XP partition, but this should get me started (I've used SuSE before, could never get video streaming to work reliably).

---

