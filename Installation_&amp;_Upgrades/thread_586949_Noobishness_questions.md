---
title: "Noobishness questions"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Amftron on 2007-10-22
Ok, so after many years of Windows based computer frolics, i have decided to take the plunge into the world of Ubuntu.

I think i should be able to handle the installation process fairly easily, but the main thing i'm uncertain about is partitioning my hard drive.

I've got a single 80 gig drive currently running Windows XP, that i want to turn into a dual boot system.  

The drive is currently formatted as FAT32.

Now, i've never really bothered to look into partitions or anything before, as i've always been quite happy with how things were, but boredom set in and i want to fiddle.

I've got about 20 gigs free that i plan on using for Ubuntu, but how am i best partitioning it ?  Should it be logical or primary ?  NTFS etc etc etc ?  

I'm not overly fussed about being able to access any data from the Windows side of things, although i suppose that would be a bonus as long as it's not too much hassle.

I'll be looking at installing 7.04 as i've not got enough ram to cope with the newest distro.

Apologies if i've missed any glaringly obvious questions or points of information, but hey, we all have to start somewhere.....

Any help is majorly appreciated.

---

### Post by justin whitaker on 2007-10-22
If the 20gb is actually free (that is empty), then just allow the partitioner to do it's thing. 

Really you want about double your RAM as a swap partition, and the rest you can set as a root (/) partition. 

The standard install is done on an ext 3 partition, but you can choose resierfs, xfs, and others. Linux does not install to an NTFS partition AFAIK. 

Make sure that you let GRUB overwrite the MBR on your machine, so you can boot both Windows and Linux.

---

### Post by Amftron on 2007-10-22
Ok, sounds fairly straightforward....only one question, as the hard drive is currently just one partition being used solely for windows, i am going to use partition magic to create a new area for this installation, should that be logical or primary ?  I'm guessing at primary....but i'm not entirely sure.

---

### Post by forestpixie on 2007-10-22
I'd use [gparted,]("http://gparted.sourceforge.net/download.php") burn it as an iso andboot with it - or the installer will do it for you if you prefer - I've read problems on here with partition magic - but that's not personal experience

If you've got room make it a primary - you can have 4

---

### Post by mivo on 2007-10-22
And defrag the disk in XP before you try to resize it (I also recommend GParted). You might even want to do that twice. This is not risk-free (the resizing), so remember to make a backup of important files, just in case.

---

### Post by forestpixie on 2007-10-22
> **mivo said:**
> And defrag the disk in XP before you try to resize it (I also recommend GParted). You might even want to do that twice. This is not risk-free (the resizing), so remember to make a backup of important files, just in case.

+1

Indeed - I also turned off the win page file after defragging to do it once more, then installed and then turned page file back on.

---

