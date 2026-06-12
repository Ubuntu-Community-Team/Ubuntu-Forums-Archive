---
title: "partitioning for dual boot"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by Catdancer on 2012-12-08
hello all, I just got a new PC and don't want to mess this up.....

it has a 320GB drive, one partition, using WIndows 7 Pro (xp mode enabled)

I want to end up with Ubuntu 12.04 and Windows 7 dual boot, AND have an independent "data" drive accessible by both OSs

I THINK the first step is to re-size the current main partition to, say, 100GB, label and format the balance 220GB as fat32 and "Data Drive" or something. THEN the second step would be to install Ubuntu 12.04 onto the 100GB partition, figuring that the installation dual boot option would split THAT drive into two, one for Win7 and one for Ubuntu. Is this right?

Or should I shrink current main partition to 50GB and create two other partitions of 50GB and 220GB each for Ubuntu and data, respectively, and then hope that Ubuntu will set itself up in the second 50GB partition?

Thoughts?

Thanks a lot

---

### Post by darkod on 2012-12-09
Don't use the installer to shrink win7 partitions, especially the system partition.

What you should do, according to what you said so far, is:
1. Use win7 Disk Management to shrink the win7 partition to 50GB. Reboot few times in case it needs to do some disk checks.
2. Create a second 220GB NTFS partition. Not FAT32, it has more limitations and you should use ntfs. Leave the rest of the 50GB as unallocated, don't create any partition from windows.
3. Start the ubuntu install and if you want to use the auto method it will automatically use the unallocated 50GB to install.
If you want to use manual partitioning, create your partitions from the 50GB unallocated space. If you are creating them manully, make the ubuntu partitions as logical, not primary.

That should be it.

---

### Post by mlentink on 2012-12-09
If you're running Win7 it is very unlikely that you're doing so on only one (1) partition. I'd advise to check carefully.

---

### Post by NightsShadeQueen on 2012-12-09
Yeah, my Win 7 setup took three partitions. That plus Linux's two and Data, meant that I needed a total of six partitions, and I think you're limited to four primary partitions.

That said:


[LIST=1]
[*]I'd take a look first - make a bootable, boot from it, look at your existing partitions with gparted, don't change anything. If your Win 7 setup is also three partitions, you'll need logical/extended partitions. Two of the Win7 partitions should be fairly small, for generalized definitions of small. Don't touch these. The largest one should be your actual Windows partition. (I don't know what the other two do; I suspect one is safe-mode, the other was labeled something like "boot").
[*]Then, boot into Windows and use the Win7 disk manager to shrink the Windows partition.
[*]Reboot several times, hope everything didn't break. If you really want to be absolutely completely paranoid (I am), run chkdsk on that partition.
[*]Then boot into the bootable and make a single logical partition that spans the rest of your hard drive.
[*]Then, in this logical partition, make your data partition (do NTFS - fat32 can't handle files larger than 4gb), a linux partition (I use ext4) and also a 4 GB linux-swap partition. Swap's...technically unnecessary, but it's not much space and it really does make a difference*
[*]Make sure your Linux partition is mounted at /, and you should be able to successfully install.
[*]And finally, make sure everything boots :D. If it doesn't, Grub is probably misconfigure. Of the multiple times I've done this type of installation, there was once when Windows decided to completely break Grub.
[/LIST]
*that said, never swap on an SSD unless you want to be buying a replacement drive pretty soon.

You'll probably want to point your home directories to Data as well, after you're done. 
Windows: [http://windows.microsoft.com/en-US/windows7/Customize-a-library](http://windows.microsoft.com/en-US/windows7/Customize-a-library)
Linux: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) although I'm pretty sure you can just skip to the point of editing /etc/fstab 

Oh, and double-check you  have ntfs-3g installed on Linux. The lack of that produces a very lovely "you don't have permissions" error message if you try to write to an ntfs partition. (Hi three hours spent going "sudo chmod 777 why won't you work you stupid backup drive")

Finally, keep your bootable. I don't know if I'm just a derp or what, but I found that my Linux wasn't particularly stable; most of this was me messing up configs or 12.04 disagreeing with my graphics driver, but having a live bootable can really help if things start going wrong.

---

### Post by Wim Sturkenboom on 2012-12-09
> **Catdancer said:**
> hello all, I just got a new PC and don't want to mess this up.....
Why not? You learn from it :)

> **Catdancer said:**
> I THINK the first step is to re-size the current main partition to, say, 100GB, label and format the balance 220GB as fat32 and "Data Drive" or something. THEN the second step would be to install Ubuntu 12.04 onto the 100GB partition, figuring that the installation dual boot option would split THAT drive into two, one for Win7 and one for Ubuntu. Is this right?

Or should I shrink current main partition to 50GB and create two other partitions of 50GB and 220GB each for Ubuntu and data, respectively, and then hope that Ubuntu will set itself up in the second 50GB partition?
Resize the main partition using Windows tools. Create your 'huge' data partition as well using windows tools and format it as ntfs. As said. leave the rest unallocated.

Be aware that your total number of primary partitions at this stage must be less then four.

Next use the Ubuntu installer to install Ubuntu; it will require two partitions.

To my knowledge, moving your Ubuntu home partition to the NTFS or FAT32 drive (as suggested by NightsShadeQueen) will NOT work.

---

### Post by NightsShadeQueen on 2012-12-09
As far as I know, each of /home, /var, etc. can be on its own partition and Linux can deal.

Couple of my friends have a setup where / is on an SSD and /home is on a old-fashioned hard drive.

---

### Post by mlentink on 2012-12-09
> **NightsShadeQueen said:**
> As far as I know, each of /home, /var, etc. can be on its own partition and Linux can deal.

Couple of my friends have a setup where / is on an SSD and /home is on a old-fashioned hard drive.

That's no problem. But putting your /home on an NTFS partition is a bad idea.

---

### Post by NightsShadeQueen on 2012-12-09
Ah. Right.

Sorry about that.

Symlink then?

---

### Post by darkod on 2012-12-09
> **NightsShadeQueen said:**
> Ah. Right.

Sorry about that.

Symlink then?

If we are being exact (and we should be), there is an error in your steps 4 and 5 in your post. You said to create one logical partition spanning the rest of the disk, and then 3-4 logical partitions inside it.

A logical partition IS a partition, you can't create one into another.
BUT, all logical partitions are inside a container called extended partition. You can have extended partition spanning the rest of the disk, and many logical partitions inside it. I guess that's what you meant.

Personally, I wouldn't create extended and logical partitions with windows in this case. Since you plan to have ubuntu logical partitions, make them from ubuntu. You can also create the shared data NTFS partition from ubuntu after you install it (or before, from the live cd). Linux does a much better job in creating partitions, and windows will read the ntfs partition created from ubuntu just fine.

---

### Post by NightsShadeQueen on 2012-12-09
Yeah, I got my logicals and extended partitions messed up: I definitely mean logicals within an extended.

And I meant partitioning the extended/logicals via the bootcd/bootable drive. 

Sigh. Been a while since I last set up that kind of system. Thanks.

---

### Post by cybrsaylr on 2012-12-09
> **NightsShadeQueen said:**
> *that said, never swap on an SSD unless you want to be buying a replacement drive pretty soon.

Why? 

I have a 128GB SSD with 2 partitions:
119GB partition with 12.04 and 8.6GB partition for swap.

What is wrong with this and what do you suggest is best to correct it?

---

### Post by oldfred on 2012-12-09
@cybrsaylr
The issue on SSD and swap always seemed to be that excessive writing might wear out a SSD. But with most users who have SSD have also spend the money to have at least 4GB of RAM, usually more and then you almost never use swap anyway. 

If you are hibernating that would be about the only time you might use swap. With lots of RAM you have to just about load every app you have. The only other case as I understand it is video editing. With video editing you cannot have enough RAM and swap as it wants to load that all into memory.

I have my swap on a rotating drive just to have some, almost never use it with my 4GB of RAM and never hibernate.

---

### Post by Pjotr123 on 2012-12-09
Nevertheless, it's wise to reduce the swappiness when you've got an SSD.... I've set it to 1 at my SSD (default is 60). How-to: [https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-swap-wear-and-tame-the-inode-cache](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-swap-wear-and-tame-the-inode-cache)

---

### Post by NightsShadeQueen on 2012-12-09
Yeah, you already have a fast HD, so you need the swap less, and you don't want to excessively write.

Also: [http://linux.about.com/library/cmd/blcmdl8_swapon.htm](http://linux.about.com/library/cmd/blcmdl8_swapon.htm)

```
swapoff -a
```

---

### Post by cybrsaylr on 2012-12-09
> **oldfred said:**
> @cybrsaylr
The issue on SSD and swap always seemed to be that excessive writing might wear out a SSD. But with most users who have SSD have also spend the money to have at least 4GB of RAM, usually more and then you almost never use swap anyway. 

If you are hibernating that would be about the only time you might use swap. With lots of RAM you have to just about load every app you have. The only other case as I understand it is video editing. With video editing you cannot have enough RAM and swap as it wants to load that all into memory.

I have my swap on a rotating drive just to have some, almost never use it with my 4GB of RAM and never hibernate.

Thanks for the explanation.
I see the hibernation feature has been removed. 
Only suspend exists. My PC is set to 'turn screen off after 10 minutes'. Is this considered part of suspend? 

Got in the habit of running System Monitor > Resources, to keep an eye on core usage when having problems with certain apps in the past. Noticed some cores would peg at 100% when running some apps, causing PC sluggishness and unresponsiveness in my i7. It was in these few cases in the past I saw some use of swap. Since I have 8 gigs of ram, swap only seems to be used when something bad, unusual or strange is going on.

---

