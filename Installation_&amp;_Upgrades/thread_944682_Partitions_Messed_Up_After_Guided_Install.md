---
title: "Partitions Messed Up After Guided Install"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by benf101 on 2008-10-11
Here's the good news: I didn't lose any data.  Now, I just have to figure out what happened to my partitions.

**Partitions Before I Touched Them:**
FAT32 10gigs
NTFS 69.xx gigs
FAT32 (I think) 69 gigs

I couldn't install Ubuntu with that setup because at 94% into the install, grub gave a fatal error and aborted the install... so I repartitioned the 3rd partition.

**Here is what I TOLD gparted to do:**
FAT32 10 gigs (leave alone)
NTFS 69.xx gigs (leave alone)
FAT32 - resize to 66 gigs, make it ext3, and make the remaining 3 gigs unallocated (for swap use and whatever the other need was)

**Here is what it gave me:**
unallocated 1gig (I didn't ask for that)
FAT32 9 gigs
NTFS 69.65 gigs
unallocated 3.22 gigs (I didn't ask for that) 
ext3 66 gigs
unallocated 3 gigs

But, I figured it's good enough to begin the install.  I figured it knew better than me.  After the successful install, which successfully dual boots, I found my partitions like this:
[IMG]http://infreedomscause.com/files/gparted.png[/IMG]

The partition that ubuntu ended up on is the small one, I believe, because I cannot upgrade to 8.1... it says I don't have enough disk space.

How do I make that mess into the right combination of drives?  An option other than a reinstall would be nice, but hey, it wouldn't be the end of the world.  Thanks to whoever can help.

---

### Post by ajgreeny on 2008-10-11
Your unallocated partitions are not GBs but MBs, so are really very small, but I can't quite see where they came from, unless they were there but you were simply unaware of that fact.  However, using gparted from the ubuntu live CD you could easily move the partitions left in the diagram you show, and then enlarge the sda3 partition to take all the unallocated space.  I have no idea what sda5 is but as it is ext3, it must be related to your ubuntu install in some way, so it would be good to know what folders and files it contains.  Your windows, I presume is on sda2 and sda1 may be a recovery partition for reinstalling windows, though 8.06GB used is rather large for that.  Finally your swap is probably too small at 196 MB; usually it would be between 512 MB and 1GB.

Frankly, if it were me and I had no real data on the ubuntu system, I would start again.  I suggest deleting the partitions to the right of sda2, then using gparted to move sda1 and sda2 backwards on the disk.  Now make new partitions for / of about 6GB, /home, if you want a separate home partition of the rest of the disk less an extended partition to contain your swap of about 1GB.  Now when you install ubuntu you can choose Manual at the partitioning stage and select those new partitions for the various mount points as I suggested.

I hope that all makes sense to you.  They are only suggestions, but if you want to discuss this further come back again.

---

### Post by Sef on 2008-10-11
> Frankly, if it were me and I had no real data on the ubuntu system, I would start again. I suggest deleting the partitions to the right of sda2, then using gparted to move sda1 and sda2 backwards on the disk. Now make new partitions for / of about 6GB, /home, if you want a separate home partition of the rest of the disk less an extended partition to contain your swap of about 1GB. Now when you install ubuntu you can choose Manual at the partitioning stage and select those new partitions for the various mount points as I suggested.

Root should be 8 - 10 GB for Ubuntu, though you can make it as small as 4 GB.

---

### Post by caljohnsmith on 2008-10-12
> **benf101 said:**
> 
I couldn't install Ubuntu with that setup because at 94% into the install, grub gave a fatal error and aborted the install... so I repartitioned the 3rd partition.

Just in case you get that 94% fatal install error again when you reinstall Ubuntu, I just thought I would mention that is (unfortunately) a known bug, but a workaround exists: simply format the Ubuntu partition to ext2 instead of ext3, and after you successfully install Ubuntu, you can later "upgrade" your file system to ext3 by doing:
```
sudo tune2fs -j /dev/sdXY
```
Replace sdXY with your Ubuntu partition. After that, I believe the only thing you will need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2". If you need help with that let me know. :)

---

### Post by benf101 on 2008-10-16
Wow, that's good to know.  I forgot to follow up with how I fixed this, so here it is...

Yes, I reinstalled from scratch, but I learned an important point.  When installing Ubuntu, do not format the partition that you want Ubuntu on.  Instead, just delete it so that it is an unformatted part of your drive.  Then, the guided install of Ubuntu "sees" the available drive space and handles it for you.

Where I went wrong was formatting the partition where I wanted Ubuntu installed.  This caused it to use the tiny part of the drive that was unformatted (which was only a few hundred MB).  The 66 gig partition was then left alone and Ubuntu was crammed into a small section and rendered useless.

So, to recap, just partition your drive and do not format the Ubuntu partition.  Let the guided installer do that for you.

---

