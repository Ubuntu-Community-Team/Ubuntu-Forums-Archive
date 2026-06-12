---
title: "Trouble with Kubuntu installation"
date: 2019-12-29
forum: Installation &amp; Upgrades
---

### Post by prrprr on 2019-12-29
I am trying to install kubuntu on about 250 gigs of unallocated space. C partition is Windows 10. 

I have been recommended to install a separate swap partition of 2 gigs; another partition of some 150 gigs for my files (which I do want to access from Windows 10 as well), and the rest on a Kubuntu partition.

OK I boot up my ISO on a flash drive, and I get to the point where I am supposed to divide up my unallocated space, and give mount points. I have no idea what to do here. I want three separate logical partitions--one for documents, one for all things kubuntu, and a third for my swap file for Kubuntu. But what would the mount points be for these? 

Also, I don't see how my files & documents partition can be NTFS with Kubuntu. Can I create this partition later in Windows 10--still, as a logical partition? In which case, I would just ignore that space in my Kubuntu partition, and just create two logical partitions (for Kubuntu & swap), and then reboot into Windows and create a third logical partition for my documents?

I need to make these logical partitions, because in addition to my Windows partition, I have two others already on this drive, a 450 meg recovery partition, and another one that I'm not sure what it is for.

---

### Post by CatKiller on 2019-12-29
You don't need a swap partition; the default swap file is just as fast.

Kubuntu can read or write NTFS partitions fine, so you can use it for data. It can't fix NTFS partitions when they self-destruct so you'll want to use Windows for defragging and chkdisk and what have you. NTFS can't handle permissions, so you can't use it for anything important. You'll need a Linux-native filesystem (like ext4) for the Linux parts. 

Kubuntu is fine with having any of its partitions within an extended partition. The only mount point that you definitely need is /, which everything else (directories or other mount points) hangs off. 

If you're creating your data partition as part of the install I would put it somewhere like /mnt/data so that it's out of the way. You can symlink to directories in that partition in more convenient places if you want to later. 

Not an issue for now but, if you're hitting partition limits, that means the drive is using MBR, which means your Windows is using BIOS. If the time comes that you find yourself reinstalling Windows and Kubuntu you should install both of them as UEFI and use GPT partitioning that doesn't have those limits. UEFI is just better than the old BIOS.

---

### Post by prrprr on 2019-12-29
OK so I will only need to create two partitions. My OS and my documents.

I will make the first partition on my free space (C partition is already windows) the OS partition. So I would mount it as */* (without the asterisks)?. 

Then, after installing Kubuntu, I boot up into Windows and format my last unallocated space as a new logical partition, and then use NTFS, and make that my documents partition.

Is this the best approach?

As far as MBR, yes Windows is booting into BIOS, I will use this until i need to reinstall Windows but someone here suggested I just stick with what I have until I need to reinstall, so that sounds good.

---

### Post by CatKiller on 2019-12-29
> **prrprr said:**
> OK so I will only need to create two partitions. My OS and my documents.

I will make the first partition on my free space (C partition is already windows) the OS partition. So I would mount it as */* (without the asterisks)?. 

Then, after installing Kubuntu, I boot up into Windows and format my last unallocated space as a new logical partition, and then use NTFS, and make that my documents partition.

Yep, that's it. You can make your NTFS data partition in advance if you want, and just set the mount point for it as part of the install, or let the installer create it. 

Doing it manually afterwards would mean that you'd need to create an entry in /etc/fstab for it to have it mounted at boot, which isn't hard but is something that the installer would take care of for you if the installer knows about that partition.

---

### Post by prrprr on 2019-12-29
In case I didn't make it clear earlier, I want my data files entirely accessible when In Windows, b/c I am not sure how much time I might be working in Windows.

---

### Post by prrprr on 2019-12-29
So before installing Kubuntu, I would use Windows to make a logical partition that is NTFS, and then go in and install Kubuntu, but be sure to set the mount point for it during the installation? 

I guess I can call it mnt/data, as you said?

> **CatKiller said:**
> Yep, that's it. **You can make your NTFS data partition in advance if you want, and just set the mount point for it as part of the install, or let the installer create it. **

Doing it manually afterwards would mean that you'd need to create an entry in /etc/fstab for it to have it mounted at boot, which isn't hard but is something that the installer would take care of for you if the installer knows about that partition.

---

### Post by CatKiller on 2019-12-29
Yep, that's fine. You'll mount your new data partition somewhere (exactly where doesn't matter that much: just wherever makes sense to you) so that you can access it in Linux, and Windows will handle it however Windows normally handles a new NTFS partition. Windows will pretend that your Linux-native partitions don't exist.

---

### Post by sudodus on 2019-12-30
I suggest that you create the data partition with NTFS from Kubuntu. You could use **gparted** or a corresponding tool in the KDE suite, that comes with Kubuntu.

If you let Windows create the partition it is likely to be a dynamic partition, which is not compatible with linux (so it would not work with Kubuntu).

---

