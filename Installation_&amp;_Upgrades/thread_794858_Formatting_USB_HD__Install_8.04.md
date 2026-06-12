---
title: "Formatting USB HD / Install 8.04"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by uguy on 2008-05-15
I have recently installed Ubunbtu 7.10 on my Dell Latitude C600 laptop by using a fresh 40 GB 2.5" HD. I have XP on the old HD and just swap drives when i want to switch between OS... I have 7.10 working pretty well and I have customized it to work the way I like.

I would like to install this setup onto a different HD on my desktop, which is already dual boot (WIN2K & XP) on hd0. I will be adding another 20 GB HD for this installation. I have already added a 500 GB Western Digital USB HD to the desktop for backup for use by both OS.

Question #1: Does the internal HD on the desktop have to occupy a certain position on either IDE cable?

Question #2: Can I copy the installed Ubuntu 7.01 from the 2.5" drive to the 500 Gig HD and then to the new internal HD (although they will be different sizes: 2.5"=40G; new HD=20G) and then alter the MBR (using GRUB?) to make it "triple boot"?? or, would a fresh install be better (maybe to 8.04?)

Question #3: if I can copy and use the 7.10 OS, what is the best program to use?? there seems to be a lot of choices in this area

Question #4: How should I set up (format & partition) the 500 Gig HD ?? It is already Fat32 (one big partition) and I know that linux and windows both can read/write in that format, but windows will not let me make NEW partitions larger than 32 GB and will not work with files any larger than 4 GB !! I was thinking of making several 32GB partitions for shared files and two large partitions: win NTFS and Linux (eg: ext2 or ext3). Maybe it would be best to leave it as is until i finish installing Ubuntu, and use it to set the 500G HD (if it can mount the USB drive)??:confused:

ANY thoughts, comments or input will be greatly appreciated !!

---

### Post by Living2007 on 2008-05-15
Your answer to Question 2 is No, it would not work.

Once you move your partition to a new drive, the system will not be able to pick up the partition becuase Grub (the linux dual boot menu) has been moved completely.

You will need to backup all your data and install Ubuntu on the 500GB HDD.

---

### Post by uguy on 2008-05-15
Thanks for your reply... but, i'm not installing to the 500 GB HD... i will be using the new internal 20 GB HD for that... i want to use the USB drive for a temporary place to copy the installation on the 2.5" HD...

also, i think i can alter the MBR by booting GRUB from a floppy and pointing to the new copied installation on the internal HD...

---

