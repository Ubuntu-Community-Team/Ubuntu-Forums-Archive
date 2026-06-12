---
title: "Ubuntu will not install to my new solid state drive"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by TrashmanL on 2010-06-12
Short history: Had a laptop with a Hardy install - my two year old knocked it on the floor and after that it no longer recognized the drive, and I could hear the hard drive read head hit the platter when it tried to read it.

I bought a new Kingston 128GB solid state drive to replace my old 40GB drive - figure it will be more robust.

I tried installing Lucid, and it stopped after partitioning the drive and was unable to format it. I attempted to use my old Hardy install disks, and had the same issue. I spent time with Kingston tech support, they had me try a few things, then RMA'd me a new drive. New drive still had the same error.

I figured something else must've broke and let it be for a while. Today, just for the heck of it, I attempted to install XP on it. Flawless. So, it's not a hardware issue. 

Any known issues with the Ubuntu installer and Laptop SATA-2 Solid State Drives? (I'll put more details in a later post if needed, don't have them at this very moment)

---

### Post by darkod on 2010-06-12
Did you try manual partitioning or only the guided methods?
Not sure how the guided methods exactly go, but if using manual partitioning you will see when creating the partitions a tick box about rounding to cylinders. You should really turn that off for SSD (it's on by default) since they've got no cylinders of course.

Also, it is advised to leave 1MB unallocated space in front of the first partition, the SSD should use it for garbage collection feature or what ever.

I would give it another go with manual partitioning.

---

### Post by oldfred on 2010-06-12
Herman has some info on SSD or flash drive install here. It was Karmic but I think most would apply to Lucid.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by TrashmanL on 2010-06-12
I tried both the automatic and the manual. Round to cylinders was on, so I'll turn that off, but I wouldn't think that would create an issue - it should just mean any value is valid, wouldn't it? I'll try it, though.

I tried another method - the GParted Live CD. Basically same results, but I was able to actually see the detailed error message (Ubuntu flashed it too fast for me to read). 

>create new ext4 filesystem
 >mkfs.ext4 -j -o extend -L " " /dev/sda8
  >sh:nice:input/output error

I've tried FAT32, ext2, ext3, and ext4, and partitions other than /dev/sda8 - basically same everytime.

Another somewhat interesting thing, with either Ubuntu CD, once the error occured I could no longer do any operations to the drive - even repartition - until I shutdown and turned the computer back on. It no longer even saw the disk there. With the GParted Live CD, I was able to try more (unformatted) partition arrangements.

I now have a working XP install on this laptop during the latest attempt, so I'm attempting Ubuntu towards the end of the disk - shouldn't the 1mb offset be taken care of already?

Also, every partition program I've used is leaving 8mb unallocated at the end of the drive that I can't touch. (That includes the XP installation program).

---

### Post by libssd on 2010-06-12
I do not have the Kingston, but recently purchased an OCZ Vertex 32gb SSD, and it behaves like any other drive. Installed 9.04, upgraded to 9.10, and did a fresh install of 10.04. 

I believe the advice about unchecking the rounding to cylinders option is incorrect; leaving this checked will result in partition alignment with memory cell boundaries, which is supposed to improve performance. SSD controllers "fake" cylinder arrangements of HDD in order to interface with an OS, so the concept of cylinders is not inappropriate.

One of the more organized descriptions of alignment is available here: **[Partition alignment for OCZ Vertex in Linux]("http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226")**.

---

