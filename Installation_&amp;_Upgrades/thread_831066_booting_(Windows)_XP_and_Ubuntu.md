---
title: "booting (Windows) XP and Ubuntu?"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by SeePU on 2008-06-16
I built a new computer and have the same drive configuration.  Obviously, I need to start over and reinstall Windows and Ubuntu.

I thought I'd use the GRUB boot loader but I'm unsure of how to begin.  I was wondering if the method is something like:

1) Install, first, small partition at the beginning of the disk (would become Primary partition #1) of 25-50MB and install Grub there (eventually)

2) Install XP SP1 (that's what I have now, retail ver.) so create Primary partition #2 of 25GB and install XP.

3) Create primary partition #3 of 25GB for future use (another Windows partition or BSD?)

4) Create 'Extended Partition' and then logical partition #1 of 20GB (?) and install Ubuntu 8.04 here

If any of this is incorrect or you know a better/more suitable method, please post and outline/describe.  If I am missing a good thread that includes instructions/methods, please refer me or provide the link.  

Thank you!

---

### Post by meindian523 on 2008-06-16
That's a meaningful way to go,specially if you delete Ubuntu partitions,then you won't be stuck with a non-booting system.What do you mean by "same drive configuration"?The small partition#1 would be mounted as /boot [or] /boot/grub in your Ubuntu 8.04 install.

---

### Post by SeePU on 2008-06-16
> **meindian523 said:**
> What do you mean by "same drive configuration"?The small partition#1 would be mounted as /boot [or] /boot/grub in your Ubuntu 8.04 install.
By 'same drive configuration', I mean that I am in effect, swapping the way the drives are being used.  I have two drives, one is 120GB  and has Windows and Linux on it.  I have a 500GB drive that is not quite half used up and the rest is free space.  I've been recommended to use that drive now as my OS drive and therefore format the partitions in and install the operating systems.  I guess the drive that was originally designated as the 1st drive (sda1 and on.. etc.) will become an extra storage drive?  The 500GB drive is newer and probably better for loading the operating systems.  However, it is considered the 2nd drive and has the sdb sequence.  

Does all that matter?  What if I rearranged the drives in the port sequence?  

Should I just leave it? 

The reason this was set up this way is that the 120GB drive was the only one originally and therefore, it had Windows installed on it (first) and then Ubuntu later (naturally).  The 500GB drive was bought for extra storage as the 120GB drive was running out of room.  

The plan or aim is to multi-boot four or more Linux distros and XP (for when I need or opt to use Windows apps).  

Does that answer the question?  Sorry to add more info and comments but I hope that clarifies things (if you care). :-)

---

### Post by meindian523 on 2008-06-16
> **SeePU said:**
> By 'same drive configuration', I mean that I am in effect, swapping the way the drives are being used.  I have two drives, one is 120GB  and has Windows and Linux on it.  I have a 500GB drive that is not quite half used up and the rest is free space.  I've been recommended to use that drive now as my OS drive and therefore format the partitions in and install the operating systems.  I guess the drive that was originally designated as the 1st drive (sda1 and on.. etc.) will become an extra storage drive?  The 500GB drive is newer and probably better for loading the operating systems.  However, it is considered the 2nd drive and has the sdb sequence.
Yup,your 120 GB will act as the second drive,assuming that you will delete your OS partitions on it before installing your OSs on the 500GB.  
> **SeePU said:**
> 
Does all that matter?  What if I rearranged the drives in the port sequence?  

Should I just leave it? 
I dunno much about hardware and HDD bays and stuff,but I believe the 500 GB should be the master(assuming both are IDE) since you are trying to boot the OS from it.I may be wrong though.Also,I've heard that Windows insists on being installed to the first partition on the first HDD to boot.I have no personal experience on that count,however,since I've only 1 HDD.
> **SeePU said:**
> 
The reason this was set up this way is that the 120GB drive was the only one originally and therefore, it had Windows installed on it (first) and then Ubuntu later (naturally).  The 500GB drive was bought for extra storage as the 120GB drive was running out of room.  

The plan or aim is to multi-boot four or more Linux distros and XP (for when I need or opt to use Windows apps).  

Does that answer the question?  Sorry to add more info and comments but I hope that clarifies things (if you care). :-)

I also think that you could just move all your data on the 120 GB to the 500 GB and use the entire 120 GB drive only for OS.Coz Linux distros require only about 8-10 GB of space each for / and you can share a common partition for /home for all the distros,with different usernames.I won't want to go into the territory of 1 username across all distros,coz there **might** be great mashup about permissions.

---

### Post by meindian523 on 2008-06-16
> **meindian523 said:**
> 
I dunno much about hardware and HDD bays and stuff,but I believe the 500 GB should be the master(assuming both are IDE) since you are trying to boot the OS from it.I may be wrong though.Also,I've heard that Windows insists on being installed to the first partition on the first HDD to boot.I have no personal experience on that count,however,since I've only 1 HDD.
Well,I just found that Grub can make Windows *feel* like it's on the first partition on the first HDD even if it isn't using the map command.It basically is:
```

grub> help map
map: map TO_DRIVE FROM_DRIVE
    Map the drive FROM_DRIVE to the drive TO_DRIVE. This is necessary
    when you chain-load some operating systems, such as DOS, if such
    an OS resides at a non-first drive.

grub> 
```

---

### Post by SeePU on 2008-06-18
If I have a dedicated or separate grub partition, does it matter if it's a primary partition or not?  Since such a partition is aimed to be small, I doubt I'd want it to be 'primary' unless it had to for some reason.  I haven't been able to confirm one way or the other or figure whether it should be a primary partition or not.  

Do you know?

---

### Post by housam on 2008-06-18
> **SeePU said:**
> If I have a dedicated or separate grub partition, does it matter if it's a primary partition or not?  Since such a partition is aimed to be small, I doubt I'd want it to be 'primary' unless it had to for some reason.  I haven't been able to confirm one way or the other or figure whether it should be a primary partition or not.  

Do you know?

About preparing your grub partition , I think you can make it a logical one as long as you have a modern HDD.

> Creating Your Grub Partition
Unless you have very strange hardware with special booting needs, you can fit all Grub code into a 1MB partition. Create the partition with fdisk. The fdisk program is able to make tiny partitions not on cylinder boundaries. Other programs such as cfdisk round to the nearest cylinder boundary, thereby making this partition much bigger than it needs to be. For the same reason, use fdisk to create the partition after this one, to make sure that no space is left in the middle. From then on, assuming partitions are big, other partitioning programs are fine, because a few megabytes on one side or the other of a 2GB partition aren't significant.

If you're working with a very old bios with the ancient 1024 cylinder limitation, it should be very near the front of the disk (make it /dev/hda1). Remember, it's only a megabyte in size, so it's not going to "push out" any other partitions with this limitation (typically the /boot partition). As a practical matter, modern bios implementations don't have this limitation, so on modern machines you can put the grub partition anywhere.

Try to make sure to remember the device number (/dev/hda1) or whatever) housing the grub partition. However, if worst comes to worst, you can quickly see which partition using this command:

fdisk -lu /dev/hda

The preceding command prints out the number of sectors used by each partition. The Grub partition will be the smallest, because no modern operating system can be housed in a 1MB partition.

Once you've used fdisk to create the partition, format it with the mkfs.ext2 command. There's no use making this an ext3 partition, because it's small enough to fsck anyway.

---

### Post by SeePU on 2008-06-18
Thanks, housam, that's the source I'm going by, too.  I just wanted to make sure.  I don't know why the author picked 1MB as it makes for more work but it's good to know.  

I think .ext2 format is used, too.  I don't know why but I found a page in which an author is saying that he acknowledges that this is used but hasn't been able to discover why.

---

