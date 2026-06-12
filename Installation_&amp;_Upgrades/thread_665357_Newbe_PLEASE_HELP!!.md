---
title: "Newbe PLEASE HELP!!"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by fasthands on 2008-01-12
I am new to Ubuntu, I am having major problems installing Ubuntu onto my hdd I have built my pc from scratch practically. I Have built it with the following hardware,
Msi 945GCM5-F ,motherboard,
INTEL CORE 2 DUO E4500 Processor,
XFX 8600GT Extreme with Zalman Fansink 256MB GDDR3 Dual DVI HDCP HDTV out PCI-E Graphics Card,
CORSAIR 2GB RAM KIT 2X 1GB,
And I have a Newlink PCI ATA133 RAID CONTROLLER CARD.
MSI 52X CD-R/RW,
E-IDE DVD writer
Western Digital 320Gig HDD. IDE not SATA.
My West/digital HDD is connected to the only IDE port on my mother board and jumper set to MASTER, and my DVD and CD-RW are connected to the Raid Card in the master slot(blue)
My graphics card is not yet fitted as I awaiting delivery, I am trying to install Ubuntu 6.10 as it is my only live CD that I have. 
I have set my bios boot sequence to boot from my DVD drive first then my HDD then CD-RW I inserted the live CD into my DVD drive OK went through the installation guide, when I git to the partition HDD part that is when the fun begins!:confused: I choose to use the setting the live CD chooses. But it says there is errors found and I need to go back and correct these so I go back and it says no root partition I need to assign a root, but there is a little icon in the screen looks like a small disk icon! and I am getting a crash alert saying "E2fsck" closed unexpecedly. How do I clear the HDD partition settings and start again? I am reading through the book, Beginning Ubuntu Linux, by Kier Thomas. And I am understanding things like using the terminal to input command lines and so on but I need help that I can't find in this book. Can anyone HELP ME PLEASE! I rely on my pc as I am disabled and house bound for months to come, due to an accident at work. Please help.

---

### Post by PmDematagoda on 2008-01-12
Are you able to get the Ubuntu 7.10 ISO image, you would have much better success with it, especially concerning your hardware.

---

### Post by djbsteart1 on 2008-01-12
if you want to edit the partitions you can always try system rescue cd or pmagix. but as it seems that you just want ubuntu installed it seems that the ubuntu partitioner would suffice.

---

### Post by fasthands on 2008-01-12
I only want to run Ubuntu on my pc I have 320gig to play with I have got Gparted running, but unsure how to partition my HDD, can anyone tell me how big each partition needs to be and what to use in the "create as and file system" option boxes. I would like to have 200gig for storage of files and use the other 120gig for the installation of Ubuntu and whatever it needs. if that makes sense!? many thanks Mark.

---

### Post by djbsteart1 on 2008-01-12
in the 120gb space, put a partition that is between 2 times ad 2.5 times the size of your ram, as its file system it should be "swap" or "linux swap". this partitions size can be changed, if you want more virtual memory increase its size (this is good if you have low ram, you dont so its not vital) the remaining space should be partitioned with a mount point of "/" as for its file system you can choose from ext3, reiserfs, jfs, xfs, or fat32 if you want windows to be able to mount the disk. look at the different options on google if possible, but all filesystems are good. ext3 is a safe but, and jfs is also n excellent choice.

---

