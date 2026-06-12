---
title: "[SOLVED] Question About FAT32 Volumes In Intrepid"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-08-30
Here is a little back story. I had Windows XP and Hardy installed each on a separate hard drive. I wanted to have the same music files accessible to both Operating Systems without having to copy the same music files twice. I have a Zune, so having the same music files on both is extremely important. In fact, if it wasn't for the Zune and Oblivion I wouldn't even need Windows.

What I did was put all my music files in the Windows XP My Music directory and then I symlinked the Music folder in Ubuntu to point to the Music folder in Windows.

This worked very well but with one huge problem. I was able to have the same exact music folder in both operating systems, but every time I saved a music file (since it was stored on an NTFS volume) it screwed up the hard drive tables in Windows and made me lose a lot of data. Yes, I was using ntfs-3G, when they say that it has 100% write compatibility, it's an outright lie.

My proposed solution is to create a FAT32 volume on my Windows drive for music only. The problem there is that I'll probably be meeting the 32GB limit with my music files or very close. I've heard that Linux can create FAT32 volumes larger than 32GB, and I also heard that was an extremely bad idea.

I just don't know what to do, so I'm mainly asking what is the best way to make Intrepid share the same music folder as Windows, but not be NTFS. I think that having Intrepid create a FAT32 volume is the only way to get around this. Yet, it's only a matter of time before my music collection reaches the 32GB FAT32 limit.

---

### Post by Naddiseo on 2008-08-30
I did it the other way around, put music on a ext2 partition and installed this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Then I just moved over to 100% ubuntu after I got an XP laptop for gaming.

---

### Post by jlacroix on 2008-08-30
> **Naddiseo said:**
> I did it the other way around, put music on a ext2 partition and installed this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Then I just moved over to 100% ubuntu after I got an XP laptop for gaming.

Would that cause a compatibility issue in Windows for Zune syncing? I think the FAT32 thing might be easier but if not I'll give that a try.

In case it makes a difference, I'll be using Kubuntu Intrepid.

---

### Post by Gina on 2008-08-30
Another possibility might be to use a network drive.  Which OS reads or writes to this drive is irrelevant as the network software handles the read/write.

---

### Post by forumache on 2008-08-30
> ... but every time I saved a music file (since it was stored on an NTFS volume) it screwed up the hard drive tables in Windows and made me lose a lot of data. Yes, I was using ntfs-3G, when they say that it has 100% write compatibility, it's an outright lie.

Interesting experience. I had the opposite: writting 8 Gb of data on a NTFS Partition from Linux, I had no errors (checked with md5sum). There were a lot of files, all kind of sizes.

I trust NTFS3G. You may have a reason to distrust it. After all it's your data. Trust/no trust, always make a backup ;)

---

### Post by RIchard James13 on 2008-08-30
I have one of those portable hard drives plugged into my computer. It has a huge 120 GByte VFAT partition on it. It is perfectly good for sharing files not only between different operating systems but also different machines. I say give a VFAT partition a try. The reason they say don't go so large with VFAT is (I forget) something to do with performance or slack space. Since you are only using the partition for sharing files the convenience out-ways any other problems for a common music partition.

---

### Post by jlacroix on 2008-08-30
> **forumache said:**
> Interesting experience. I had the opposite: writting 8 Gb of data on a NTFS Partition from Linux, I had no errors (checked with md5sum). There were a lot of files, all kind of sizes.

I trust NTFS3G. You may have a reason to distrust it. After all it's your data. Trust/no trust, always make a backup ;)

Here is a more detailed experience of what ntfs-3g did to me.

I have an Nvidia SLI set up. Every time I saved files to my Windows drive from within Ubuntu, if I ran a disk check in Windows, it would pick up a bunch of index errors and say its deleting stuff. Then, ironically, the stuff it deleted was my Nvidia driver and I'd have to reinstall the Nvidia driver after the disk check ran.

So basically:

1.) Save files to the Windows drive from within Ubuntu
2.) Run a disk check in Windows
3.) Windows reports errors
4.) Nvidia driver needs to be reinstalled.

It happens 100% of the time like that for me. When the Nvidia driver needs to be reinstalled, Windows defaults it back to the VGA 640*480 driver.

---

### Post by kahping on 2008-08-30
> **jlacroix said:**
> My proposed solution is to create a FAT32 volume on my Windows drive for music only. The problem there is that I'll probably be meeting the 32GB limit with my music files or very close. I've heard that Linux can create FAT32 volumes larger than 32GB, and I also heard that was an extremely bad idea.

There are windows tools to format larger than 32GB FAT32 partitions including Partition Magic. But even Partition Magic artificially limits you to ~220GB IIRC.

Have you tried [this]("http://www.ridgecrop.demon.co.uk/index.htm?fat32format.htm")? I've used it before with no problems so far

Alternatively, you could use a Win98 bootdisk and format from there? Then you'd at least have a 64GB limit which is better than 32GB :)

---

### Post by cariboo on 2008-08-30
I've got a 320GB external that is formatted as vfat, it has been running for so long I forget how I formatted it. I know it was before Linux could write reliably to NTFS. 

I also use a 160GB external eSATA drive that is formated as NTFS for a data drive. I just recently transfered all my mp3's, about 70GB, and had no problems.

Jim

---

### Post by jlacroix on 2008-08-31
Well I decided to just go with a 32GB FAT32 partition. I can live with it I guess.

Even worse, the problem I was having with Linux corrupting my Windows XP drive, that was not Linux' fault at all, I'm still having that problem in Windows and I'm about to throw something!

I know this isn't a Windows board so if anyone wants to help solve a really challenging X-File, email me. 

Other than that, I guess this part is solved.

---

### Post by Gina on 2008-08-31
As it's off topc, I'll just say .... always shut down Windows properly otherwise if you write to it's filesystem it may get upset and lose data next time it is run.

---

