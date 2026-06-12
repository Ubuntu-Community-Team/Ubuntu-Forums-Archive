---
title: "Needing patitioning advice"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by 3lud13 on 2011-09-15
Im about to get a new hard drive and am looking at dual booting again with windows for those times my windows friends need assistance with stuff and a few other things Im still finding easier in windows. im wanting my documents on a seperate partition to the actual OS so layed out below is how I think it should work. also I know Linux needs to be ext 2 or something but can my files be say a fat32 or something so windows can read them. I guess also in there somewhere I need a partition for the bootloader also but this is what i have so far

partition   File System    Label        Size
1             Extended                         54Gb
2             Linux-Swap                     4Gb
3             Ext2                /                50Gb

4             Ntfs                Windows   30Gb
5             Fat32             /home        remainder

---

### Post by 2F4U on 2011-09-15
You should choose ext4 instead of ext2 but else you can go ahead with that partitioning scheme. It is not necessary to reserve 50GB for Linux, but that doesn't hurt and depends on what you intend to into that partition.

---

### Post by Blasphemist on 2011-09-15
Here is what I'd do. 
1. Install windows. If you are going to have windows, its best to install it first. Windows isn't as easy to guide to a partition as Linux is.
2. With windows already installed, boot to the live CD/DVD/USB or the Linux distro and run the GParted application. Use GParted to shrink windows to the desired size. This will leave un-allocated space.
3a. One of your options is to now choose to install Linux. Linux will then present an option to use the un-allocated space. Linux will then create an extended partition and within it logical partitions for swap and another for everything else.
3b. There is another option to do more of the configuration in GParted. You would create the extended partition using all of the un-allocated space. Within that partition you would create logical partitions. Logical partitions for Linux distro / (root) mount points need to be at least 5GB but should be 10-15 GB. This allows for enough space to add any software you may need and some room for documents. If you will need room for a bunch of pictures, video, documents, music, etc., add room for that to the 10-15. 
3c. You should determine if possible what your future plans are. For example, I have 7 distros installed into their own partitions, all within the extended partition. I also have a partition for sharing documents, pictures, music, etc. between all distros and windows. Many people recommend using a separate partition for you /Home directory instead of having that in the same partition as the rest of that distro. I don't do that as it would make my partitioning very busy and it can waste disk space if you don't plan the space very well. I also don't see that as needed when I have the shared partition.

All Linux partitions are generally formatted as EXT4 these days. Windows can't access EXTx partitions but Linux can access partitions formatted in what windows prefers, NTFS or FAT32. NTFS is the best choice for the format of any partition that will be shared by windows and Linux. These shared partitions should be created as logical partitions within the extended partition. It's best to create one swap partition at the end of the disk that is a bit more than the amount of memory you have or expect to have. If you have more than one distro, all of them will use the swap partition without you even having to tell them to do that.

Some Linux distros vary in some ways from what I've described here by default but can be told to follow this. An example is Fedora. But for all Ubuntu based distros this applies.

---

### Post by Sef on 2011-09-15
> partition   File System    Label        Size
1             Extended                         54Gb
2             Linux-Swap                     4Gb
3             Ext2                /                50Gb

4             Ntfs                Windows   30Gb
5             Fat32             /home        remainder

Windows needs to be a primary partition - preferably the first. I would make the swap equal to your ram in case you want to hibernate or suspend. Use EXT4 for Linux and NTFS for Windows as Linux can read NTFS with some software that is installed on Ubuntu (currently) by default. (You might need to add NTFS-3g.) Create a home partition, so that the files can be saved separately from the OS.

---

### Post by srs5694 on 2011-09-16
There are many ways to do this, and others have provided reasonable suggestions. A few more from me:


[LIST]
[*]Generally, Ubuntu can install to partitions as small as about 5 GiB, but on any but a dinky hard disk, ~20 GiB is a better size, since it gives more room for installing lots of software. This size refers to the OS system files alone, not to user data files, which can range from tiny to huge.
[*]I recommend a swap partition that's *slightly larger* than the computer's RAM. The reason is that it's easy to confuse gigabytes (GB) and gibibytes (GiB), and if you size the partition in GB, it could actually be slightly too small to support the suspend-to-disk feature.
[*]I recommend using a separate /home partition. In a Linux-only installation, it should be all the remaining disk space after allocating space for root (/) and swap. In a dual-boot configuration, you also need to consider space for the other OS and for your shared-data partition. If you expect to be sharing *all* your user data, then a separate /home partition might not be worth creating -- see my next point.
[*]You cannot use FAT or NTFS as a /home partition's filesystem. This is because Linux relies on filesystem features in users' home directories that FAT and NTFS don't support. Thus, you must mount a shared-data partition elsewhere and either use a distinct Linux /home partition or omit that partition and leave the /home directory as part of the root (/) partition.
[*]FAT is the most compatible filesystem for sharing across OSes; however, it's a pretty ancient filesystem and it has significant limitations. The most important of these is probably its 4 GiB file-size limit, which is an issue if you expect to store large files like DVD images, system backup files, or big multimedia files on the disk.
[*]For these reasons, NTFS is often used as a Windows/Linux shared-data filesystem. It works, but it's slower than FAT under Linux (although it's faster than FAT under Windows).
[*]I strongly recommend keeping a separate shared-data partition rather than letting Linux access the Windows boot [noparse](C:)[/noparse] partition on a regular basis. The reason is that it's too easy to accidentally trash the Windows boot files from Linux if you access the Windows boot partition on a regular basis. Putting your regularly-accessed shared files on a separate partition minimizes the risks of such cross-OS accesses, since you'll at least be accessing a less critical partition.
[/LIST]

---

