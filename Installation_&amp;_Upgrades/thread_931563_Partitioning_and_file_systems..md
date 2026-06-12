---
title: "Partitioning and file systems."
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by gregkarr on 2008-09-27
I am preparing to install Ubuntu on my brand new laptop that has Vista on it. After doing some reading about partitioning the hard drive, file systems etc., this is how I plan to proceed when partitioning my 160 GB hard drive:

Partition 1: Vista, 28 GB, Primary, NTFS
Partition 2: Ubuntu Root, 8 GB, Primary, ext3
Partition 3: Data, 116 GB, Primary, NTFS(??)
Partition 4: Extended ---> 
  Partition 5: Swap, 8 GB, Logical, ext3

The plan is to have a simple dual boot system with Vista and Ubuntu, and to use the Data partition for all my documents, music, videos etc. I want to be able to access all of these things from both Vista and Ubuntu though, so the question is a) if this is possible as long as I make it an NTFS partition, and b) is this a good idea? My understanding is that partitions 2 and 5 will be invisible to Vista, but that Ubuntu will be able to access all of them. I guess my concern is that it may be really inefficient or something in linux to have all the data stored on an NTFS partition?

Oh, and I have 4 GB of memory, and read that the swap should be twice that. Does that still hold when I have that much memory, or is that a bit of a waste?

Any comments or tips would be much appreciated.

---

### Post by Partyboi2 on 2008-09-28
I think you probably be ok with 3 gig for swap, 8 gig is to large. Ubuntu can read/write to ntfs so your data partition should work well. You could also make the extended partition as partition 2 instead of partition 4

---

### Post by gregkarr on 2008-09-28
Thanks for the reply! 

> You could also make the extended partition as partition 2 instead of partition 4

Is there any particular reason why I would want to do that? What difference does it make? 

My final question is whether I should add a boot partition (and if so, I guess it must be a primary partition and that I should make the Data partition logical)?

---

### Post by alexgieg on 2008-09-28
I'd suggest placing the swap near the middle of the hard disk, or somewhere in its first half. This way the magnetic head won't have to move to much away from where most of your data resides (i.e., all the way to the disk's extremity) when virtual memory is needed.

As for whether to use primary or extended partitions, or what to put where, Linux doesn't care either way. You could have all your partitions, including the boot one, inside an extended one, and it would work without a complain. Arbitrary limitations such as the boot partition having to be primary are typical of the Windows world, not of the Linux one. :)

---

### Post by zeryth on 2008-09-28
i think you should use fat32 instead of ntfs...

---

