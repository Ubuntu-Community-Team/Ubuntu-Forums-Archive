---
title: "Ok, ready to install Linux Mint, please help me out."
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by ogwilson on 2008-02-13
Ok, So I downloaded Linux Mint, and I've partitioned my harddrive as follows:
 
160gig HDD:
 
25gigs - Windows XP SP3, NTFS
25gigs - Linux Mint, ext3
100gigs - Music, Media, Etc, FAT32
3gigs - Swap Partition, swap
 
Obviously these are dark figures as far as the actual sizes go, but you get the idea.
 
Anything wrong with that? Is the swap partition too big? Am I using the recommended file system for each partition? Are there any other partitions I might need?
 
Also, I had a problem before when I installed Ubuntux: GRUB took over my PC and I couldn't boot the way I wanted to, not even from a boot disc. If I install WinXP first, then Install Linux Mint, will GRUB behave that same way? How can I prevent it from taking over like it did before? I just wanna be able to boot into XP AND Linux with ease, as well as any bootable discs or thumb drives I may use.
 
I heard of people overriding grub and using the Windows OS selector, how can I do this? Thanks in advance.

---

### Post by jan quark on 2008-02-13
installing windows first and then linux mint should not lead to any problems with the grub loader

had done this combination many times and without a single problem

the partition plan is completely up to you, I see no problems with this

perhaps you will have to mount your ntfs and fat32 partition but that is a topic which is very popular in this forum and you will get help immediately and form everywhere

so go on

---

### Post by Existentialist on 2008-02-13
How much RAM are you running in your system?  3GB may be more space for swap than you need if you are running 2+GB of RAM.

---

### Post by ogwilson on 2008-02-13
1.5 gb

---

### Post by Existentialist on 2008-02-13
I wouldn't run more than 2GB of swap.  I don't know how tight you will be on space as it's only one gig difference.

Also do you plan on separating out your partitions in linux by running an extended partition for the linux install?

---

### Post by ogwilson on 2008-02-13
> **Existentialist said:**
> I wouldn't run more than 2GB of swap. I don't know how tight you will be on space as it's only one gig difference.
 
Also do you plan on separating out your partitions in linux by running an extended partition for the linux install?
Im not particularly too sure on what you mean and how to do what you said. Care to explain?

---

### Post by Existentialist on 2008-02-13
Well any hard drive can have at most 4 partitions.  In order to extend this these partitions can be whats called an extended partition which is a container that allows for more partitions within it.  To the OS the partitions will appear as any other partition would.  My system drive is partitioned similar to yours, but this is how I would partition yours.

25gigs - Windows XP SP3, NTFS - primary partition

28gigs broken up as follow for linux
2gigs swap - extended partition
128megs - boot - ext3 - extended partition
8gigs - / - ext3 - extended partition 
~18gigs - /home - ext3 - extended partition

100gigs - Music, Media, Etc, FAT32 - primary partition

Breaking up the different parts of linux is a more advanced and secure away of setting up the linux partitions.  Preferably you would break it up even further then that, but thats a good enough start.  All you really need to run linux is the boot, swap, and / (root) partitions as this will contain the whole os, the /home mount point is where you home directory is mounted and will hold any files you save to your linux desktop or home folder.  You could make this smaller and put more space to your FAT32 partition if you think you wont need to store that much on the linux home directory.

---

### Post by Existentialist on 2008-02-13
I probably just make things a lot more complicated then necessary for you.  You could also just do:

26gigs - windows - ntfs
26gigs - linux - ext3
2gigs - swap
100gigs - other - ntfs or fat32

For the average user this is a lot simpler and good enough if you aren't using the computer for any server tasks or anything other than general use.

---

### Post by ogwilson on 2008-02-13
Thanks for the suggestion. No, not doing much server tasks. I will mainly be using the OS for school (practicing at home + programming). So I'm installing Mint as we speak, I'll let you know how it goes.

---

