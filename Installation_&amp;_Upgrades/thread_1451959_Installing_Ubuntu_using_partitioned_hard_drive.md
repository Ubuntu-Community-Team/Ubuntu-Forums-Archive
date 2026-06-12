---
title: "Installing Ubuntu using partitioned hard drive"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by Julius2 on 2010-04-11
OK, so I want to install Ubuntu on my laptop. The thing is I want to keep the Windows 7 OS as well. I know that this can be achieved via partitioning the drive and using dual boot (I don't want to mess with virtual pc stuff), correct? Now I have this sort of diagram in my head, but I don't know if it will work. There are currently two partitions: one for Windows 7 (system only) and another one for general storage space-NTFS-(I checked with disk management). There is no unallocated disk space, but I read somewhere that during the Ubuntu installation (or the parition editor which can be used without permanently installing the OS) allows you to partition your disk. So I plan to partition the disk like this: 

Windows 7/shared Storage space (ntfs but might be converted to fat32*)/Ubuntu(ext3)/swap. 
*can I do this during ubuntu installation without losing my files?

So
--Is this going to work? 
--When I boot, will I be asked to chose the OS I want?
--Will both operating systems be able to read the fat32 or ntfs space?

I also heard that Ubuntu can read ntfs but with some problems. And that fat32 can have disk errors while ntfs is more trustworthy. Should I really convert the patition to fat32 (I suspect my files will be lost...)?

---

### Post by mifi on 2010-04-11
> **Julius2 said:**
> [...] So I plan to partition the disk like this: 

Windows 7/shared Storage space (ntfs but might be converted to fat32*)/Ubuntu(ext3)/swap. 
*can I do this during ubuntu installation without losing my files?

So
--Is this going to work? 
--When I boot, will I be asked to chose the OS I want?
--Will both operating systems be able to read the fat32 or ntfs space?

I also heard that Ubuntu can read ntfs but with some problems. And that fat32 can have disk errors while ntfs is more trustworthy. Should I really convert the patition to fat32 (I suspect my files will be lost...)?
I would like to suggest one more partition for /home. This is were all you personal files and setting are. If you keep /home separate from the rest of Ubuntu, it is far easier to reinstall or upgrade later.

To answer your questions:
> **Julius2 said:**
> 
So
--Is this going to work? 

Yes. I have done it dozens of times, albeit not with 9.10 or 10.04 (the new grub).

> **Julius2 said:**
> 
--When I boot, will I be asked to chose the OS I want?

yes.

> **Julius2 said:**
> --Will both operating systems be able to read the fat32 or ntfs space?

I have not had problems with either of them in the latest Ubuntu's. Just give it a try.

Make backups first.

m

---

### Post by SecretCode on 2010-04-11
Agree with the above.

> **Julius2 said:**
> I also heard that Ubuntu can read ntfs but with some problems. And that fat32 can have disk errors while ntfs is more trustworthy. Should I really convert the patition to fat32 (I suspect my files will be lost...)?

I don't believe fat32 is more trustworthy. The only problems Ubuntu is likely to have with ntfs is that it does not hold file permissions like ext* and other *nix filesystems - and the same is true of fat32.

Moreover, fat32 can't hold files bigger than 4GB - which might affect video files & will definitely affect virtual machine images if you go there.

---

### Post by Mark Phelps on 2010-04-11
Not really clear on your proposed partitioning scheme, but I would suggest the following:

1) Create a separate shared partition; do not plan on sharing the Win7 OS partition.  That's asking for trouble.

2) Shrink the Win7 OS partition (the SECOND Win7 partition) using the Win7 Disk Management utility to leave unallocated space for creating the Ubuntu partitions.  Don't use the Ubuntu installer to do the Win7 partition shrinking.

3) Boot into Win7, run the Backup utility, create an burn a Win7 Repair CD.  This will come in handly later should you need to repair your Win7 boot loader.

---

### Post by Julius2 on 2010-04-11
> **Mark Phelps said:**
> Not really clear on your proposed partitioning scheme, but I would suggest the following:

1) Create a separate shared partition; do not plan on sharing the Win7 OS partition.  That's asking for trouble.

2) Shrink the Win7 OS partition (the SECOND Win7 partition) using the Win7 Disk Management utility to leave unallocated space for creating the Ubuntu partitions.  Don't use the Ubuntu installer to do the Win7 partition shrinking.

3) Boot into Win7, run the Backup utility, create an burn a Win7 Repair CD.  This will come in handly later should you need to repair your Win7 boot loader.

Currently there are two partitions: One which contains only the Win7 system files and the other one which has the other files (and is managed by Win7 since it's the only OS installed). So do I shrink the second one in order to create unallocated space for the Ubuntu system files, a /home partition, swap space _*AND*_ a new partition which will be the shared one?

So in order to clarify, which of the following will represent my HDD after I complete the installation?

a.Win7 system files (currently exists)
b.Win7 managed storage space (currently exists)
c.Ubuntu system files (will be created)
d./home (will be created)
e.Shared space (for both Win7 and Ubuntu) (will be created)
f.Swap space (will be created)

OR

a.Win7 System files
b.Shared space (currently managed by Win7)(for both Win7 and Ubuntu after the installation is complete)
c.Ubuntu System files (will be created)
d./home (will be created)
e.Swap space (will be created)

---

### Post by Hobgoblin on 2010-04-11
> **Julius2 said:**
> So do I shrink the second one in order to create unallocated space for the Ubuntu system files

Yes, then install Ubuntu to the unallocated space. You can put /home on it's own partition during the install if you wish.

I would use the 2nd Windows drive for shared files, leave it as NTFS.

---

### Post by Julius2 on 2010-04-11
> **Hobgoblin said:**
> Yes, then install Ubuntu to the unallocated space. You can put /home on it's own partition during the install if you wish.

I would use the 2nd Windows drive for shared files, leave it as NTFS.

so once ubuntu is installed it will also start managing the space that windows is currently managing?

---

### Post by Julius2 on 2010-04-11
anyone? help please...

---

### Post by Slim Odds on 2010-04-11
> **Julius2 said:**
> so once ubuntu is installed it will also start managing the space that windows is currently managing?

This does not make sense. Nobody is "managing" the space. Either OS can use/change files in that space. You'll have to make some changes to /etc/fstab if you want Ubuntu to mount that partition by default.

Also note that most Windows 7 laptops come with 3 partitions initially. 2 for Windows 7 (a boot partition that is separate from the main windows install partition) and one "restore" partition that contains a copy of all the data needed to restore the laptop to factory condition.

Also, most laptops come with a program to create DVD's from this partition. I'd definitely make sure to do that!.

I installed Ubuntu into that "restore partition" after making the backups. It was about 12GB.

P.S. Don't expect answers in under an hour around here.

---

### Post by confused57 on 2010-04-11
As Mark Phelps mentioned, you should only resize your storage partition with Windows 7 partitioner and create a Windows 7 rescue cd( a Google search for "Windows 7 Rescue Disc" will give you instructions).  The second option you mentioned above should work.

What size hard drive do you have, and how large is the storage partition?  This will help anyone give you suggestions on how large to make your Ubuntu partitions...you can only have 4 primary partitions on a hard drive, so it would be advisable to make them logical partitions inside an extended primary partition.

Don't be in a hurry to start installing, do your homework & wait for some other suggestions.

---

### Post by Slim Odds on 2010-04-11
> **confused57 said:**
> ...
Don't be in a hurry to start installing, do your homework & wait for some other suggestions.

+10 for that one.

That is why there are SO many posts here that say "I did this or that and now my system is all screwed, please help me"

---

