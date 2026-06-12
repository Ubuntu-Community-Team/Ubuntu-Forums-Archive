---
title: "Partitioning is messed up in a way I don't understand"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-03-16
After yesterday's adventures (see [http://ubuntuforums.org/showthread.php?t=1426596&page=2](http://ubuntuforums.org/showthread.php?t=1426596&page=2)), my partitioning is somehow messed up and I cannot figure out how to fix it. I need to install Lucid again for this weeks testing.

What I discovered when I tried to install this morning was that my extended partition had become resized all the way to the end of the disk. So, using Karmic LiveCD, I resized it back to where it belongs, seemingly giving me 25 GB of unallocated space for my Lucid install. However, when Lucid partitioning starts and I tell it to use the largest available free space, it tells me it cannot create a partition because partitions cannot overlap.

Here is my current partition map after my attempted fix. Why won't the Lucid installer partitioner use the unallocated space?

Tim

---

### Post by Digital Hick on 2010-03-16
WOW:shock:

My humble suggestion...  :popcorn:


Provided you have no important data that can be lost.  Start a reinstall, when it gets to the partitioning part, go into the manual partitioning and delete everything, then backup to the automatic choices and tell it to use the whole disk.

Ubuntu only makes a root and a swap I think, and if you got the RAM you do not even need a swap.  I did not have one on 9.10.

---

### Post by ratcheer on 2010-03-16
Ummm, thanks, but no thanks. My main Karmic is installed on sda1, sda2, and sda5. I just need to install Lucid in the extra space for my Ubuntu testing team work. I have been doing this over and over for about a month. Until now.

Tim

---

### Post by Digital Hick on 2010-03-16
OK, try squeezing the unallocated space out of sda3 and giving it to the empty area after sda3 and try again.  If it will not recognize it under largest unallocated, do it manually with just a root and a swap.  In fact, you can share swaps I believe, so you do not even have to create a second one.

:popcorn:

---

### Post by Didius Falco on 2010-03-16
You can definitely share swap - I use the same swap partition for six different Ubuntu installs.

---

### Post by ratcheer on 2010-03-16
Okay, I'll try that. Thanks.

Tim

---

### Post by ratcheer on 2010-03-16
Ok, that worked. I still was not able to have Lucid do guided partitioning to use the largest contiguous free space, but it did let me partition theunallocated space manually.

The installation ran to completion, but will not boot. It takes me to the Lucid grub menu where, if I enter "ls", it shows seemingly correct info. But, if I enter "boot", it responds "error: no loaded kernel".

But anyway, the partitioning problem is mostly solved. I am back to Lucid installation problems.

Thank you,
Tim

---

