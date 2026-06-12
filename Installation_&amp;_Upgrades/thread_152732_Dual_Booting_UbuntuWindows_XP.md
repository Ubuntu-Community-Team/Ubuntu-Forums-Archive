---
title: "Dual Booting Ubuntu/Windows XP"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by Blazeix on 2006-03-30
Alright, I know there have been many threads about dual booting, and I have searched around in the forums and I am fairly sure how to do it. I would just like a confirmation of that these are the correct steps. I have an existing XP installation that I would like to keep. I have a 60 gig hard drive (NTFS) with Windows XP installed. 

[LIST=1]
[*]First I will backup all my important files in windows and defrag my hard drive.
[*]I am planning to resize/repartition it so there is 29Gb for windows xp (NTFS), 1Gb where I can access files from both OSs (FAT32), and 30Gb for Ubuntu (EXT3). I will use a windows program called PartitionMagic to nondestructively repartition/resize it 
[*]I will install Ubuntu on the 30Gb EXT3 partition.
[/LIST]

Now, the only question I have is about boot loaders. If I do the above steps, will the Grub bootloader be presented to me, or will it be the Windows bootloader? Thanks for any help.

EDIT: Actually, I just saw a post where it stated that Ubuntu can automatically resize the windows partition and install itself in the free space. Does this mean that I only need to make the FAT32 partition?

---

### Post by ispmarin on 2006-03-30
Your steps are right, but you can try to resize the partition with ubuntu. I never tried, I used the Partition Magic tatic. I just would change the EXT3 partition to Reiserfs... otherwise I would do exactly the same thing. The bootloader will be then grub.

---

### Post by Irony on 2006-03-30
This is the simplest way of setting up a dual boot on an existing windows partition;

[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

I've tried it and it works. Basically the install shrinks your windows partition and then you can let it automatically create partitions for ubuntu.

For more options see;

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

