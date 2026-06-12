---
title: "clean install ? i386 or amd64. and partitioning on fresh install"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by evotux on 2007-06-04
Hello, 

sorry if these have been asked but i have spent hours looking for the best way to install ubuntu.

i have the 386 and amd64 cd but was wondering what one is best to install.

and how do i set up the partitioning for the best results, i have installed ubuntu already but dont remember if i have installed the i386 or amd 64 version, i know silly, but i have read best not to have just one partition, as i have now,  especially as running as root is like running as admin in windows ( although i always do) but ubuntu might operate better not like this.

i am only installing ubuntu on my acer laptop acer ferrari amd64 bit 3000+, and have no desire to dual boot to windows as that will make me better to use ubuntu to its best ability.

sorry for the long questions but better to do it once.

thanxs for any help

---

### Post by vanadium on 2007-06-04
1) Use i386 for compatibility purposes. Many applications do not yet run 64 bit.
2) Just run the graphical install CD and let it use the entire disk. Do not worry about separate partitions for a desktop system. You will have the greatest flexibility with just one partition.

---

### Post by evotux on 2007-06-05
Thank you vanadium, i was going to reinstall, but since everything is working so far, i havnt tried the wireless set up , but i will soon , but i wont really use it just good to see if it goes.

thanxs again , and now im going to spend the night getting samba going to connect to other computers at home.

cheers vanadium

---

### Post by Mad_Max_1412 on 2007-08-29
Hi Guys,

I have seen Vanadium's response that a single partition is all that's needed for a desktop version, but I've also read in a magazine that there should be 3 partitions - one for the OS, one for swap and one for the user.

Currently I'm running everything on one partition, only because when I first installed Ubuntu it was because the magazine I mentioned before (over a few articles) made Ubuntu look a lot more friendlier than I imagined and wanted to give it a go.

I had grabbed the live CD and by following the instructions at [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) but I do recall getting confused over step 5, trying to partition it into 3 partitions as recommended by the magazine, so I only ended up with one partition.

If, and only if, people wanted to install with multiple partitions, do you think the instructions at this page ([https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)) could have step 5 modified/added to show step by step how to create multiple partitions and to designate specific ones as the swap or OS or User partition?

The instructions show how to create 2 partitions by using the slider, but doesn't say whether the first or second partition is going to be the swap partition, nor does it say how to make a 3rd, 4th etc partition.  The screenshot in Confirmation shows Partition #6 being the swap partition (would be nice for it to also confirm the size of the partition) and I gather that ext3 is the name for the partition used by the OS (and user files)?  Once again, a bit of extra info on this confirmation page saying the size of the partition would be good.

BTW, In the screenshot of select a disk, I can work out that /dev/IDE is for an IDE drive and /dev/sda is for a SCSI drive, but what would it be for a SATA drive?

Regards

---

### Post by lisati on 2007-08-29
and don't forget to make a backup of important data **before** you do the install.

---

