---
title: "Disk imaging Tools"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by deamon_knight on 2010-10-24
I'm looking for some advice in locating some disk imaging tools that are compatible with Linux/Ubuntu. In the Windows world, I use Norton Ghost to make disk images of a system after I've finished configuring it so I have something to fall back on, and I do the same thing before I make any major upgrades. With Ghost, I can pull the Hard Drive out of one system, connecting it to another running system and use ghost to make a disk image on the second system, or clone the data to a third fresh disk, even if that disk is a different capacity. Ghost can also compress the images as part of the process. I know ghost has other features, like pushing an image to several other systems simultaneously over a network, but I'm not looking to do that.

So If I want to simply make a compressed Image of a working Drive, then clone that image to a different drive, how can I do that? can I do this from a Live CD? Can I do this on a dual boot system (say windows/linux) or from a RAID array?

I've seen tools Like Clonezilla or G4L, which is good but seems more geared to the situation of cloning many of the same system from one original rather than managing many different systems.

I know I've asked a lot but any assistance is appreciated.

---

### Post by crjackson on 2010-10-27
I'm a little confused by your post. I'm not exactly sure what your goal is.

If you want to make a small, compressed disk image or partition image of a drive or partition, and store the image to another drive or device, then I would go with clonzilla.

I've used MANY disk imaging applications (windows, linux, mac). I love the look of Acronis TrueImage Workstation but it's not free and it doesn't play nice with ext3/ext4. It will back them up but it's HUGE and SLOW because it must use RAW mode.

The most up to date and FASTEST application I've found is clonezilla, and it works with EVERYTHING I've tried. It's not very pretty but it does the job well and does it fast/small. I've used it 4 times today already.

---

### Post by Mark Phelps on 2010-10-27
Clonezilla, as the name implies, can certainly be used to clone disks, but it also has an Image mode where it can be used to create a compressed image of a partition.  This is generally used as a form of backup/restore -- in a manner similar to Ghost.

But one limitation of Clonezilla is that to restore an image to a different drive, it must be large enough to hold the original partition.  Thus, say you image a 250GB partition that is only half-full, and that compresses down to a 100GB image.  If you then mount a 160GB drive and try to use Clonezilla to restore the partition to THAT drive, it will tell you it can't -- even though the drive actually IS large enough to hold the USED portion of the partition.

---

### Post by Megaptera on 2010-10-27
If you want to make a CD/DVD backup, then have a look at Remstersys:

[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

very useful!

---

### Post by deamon_knight on 2010-10-31
I've used Clonezilla but run into a few problems. As you mentioned, it won't let resize partitions as you restore an image, esp. to a smaller disk. This isn't a huge problem with Linux file systems but it is  a problem with mixed or windows environments. The Bigger problem I have is I can't seem to find it in repos. Am I doing something wrong?

Thanks for the link Megaptera, thats a solution to another problem I've been looking for!

---

### Post by Quackers on 2010-10-31
You would need to go to their website to download it.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Megaptera on 2010-11-01
> **deamon_knight said:**
> 
Thanks for the link Megaptera, thats a solution to another problem I've been looking for!

You're welcome!

---

### Post by entropy1 on 2010-11-01
Have you considered using Partimage [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

It is part of SystemRescueCd [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) which you can put on a flashdrive or CD.

---

### Post by crjackson on 2010-11-01
> **Mark Phelps said:**
> Clonezilla, as the name implies, can certainly be used to clone disks, but it also has an Image mode where it can be used to create a compressed image of a partition.  This is generally used as a form of backup/restore -- in a manner similar to Ghost.

But one limitation of Clonezilla is that to restore an image to a different drive, it must be large enough to hold the original partition.  Thus, say you image a 250GB partition that is only half-full, and that compresses down to a 100GB image.  If you then mount a 160GB drive and try to use Clonezilla to restore the partition to THAT drive, it will tell you it can't -- even though the drive actually IS large enough to hold the USED portion of the partition.

Clonezilla will compress the image down to a very small size, but as you mention, I've not tried to restore to a different sized drive and/or partition.

Acronis True Image Home 2011 has added support for EXT4 and I'm told it will do exactly what you are looking for. I'm going to download the trial version and see what happens. The problem I've always have with Clonezilla is that I dual-boot on my laptops. Clonezilla won't compress the image down to size on mixed file systems. Therefore it makes a sector by sector copy which is very large and very slow.

I'll let you know what happens with Acronis True Image. I have older versions that quit working with EXT3/4 except for sector copy. I always installed on a windows system and created a bootable media CD.  The bootable media is a Linux Disc anyway so I don't understand why they don't just sell THAT for us linux home users.

---

### Post by crjackson on 2010-11-01
> **entropy1 said:**
> Have you considered using Partimage [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

It is part of SystemRescueCd [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) which you can put on a flashdrive or CD.

partimage is incorporated into clonzilla already.

---

### Post by crjackson on 2010-11-02
Okay, I've purchased Acronis TureImage Home - 2011 and it works perfectly. It will do exactly what you are looking for.

Nice app...

---

### Post by deamon_knight on 2010-11-04
Thanks Crjackson thats good info. But this is all from live media, correct? I was looking to use an already installed system so I had GUI tools to sanity check what disk/partition I'm copying. I've wiped the wrong drive more than once myself, and running Ghost from within windows has eliminated that problem for me. Any way to do this easily within Linux?

Thanks again.

---

### Post by crjackson on 2010-11-05
> **deamon_knight said:**
> Thanks Crjackson thats good info. But this is all from live media, correct? I was looking to use an already installed system so I had GUI tools to sanity check what disk/partition I'm copying. I've wiped the wrong drive more than once myself, and running Ghost from within windows has eliminated that problem for me. Any way to do this easily within Linux?

Thanks again.

This is from a bootable livecd, HOWEVER...  They do have a Linux Server version but it's costly. You can contact Acronis and they will provide you with a trial Ubuntu installable version link via. email. That version will should do what you want.

On the cheap side of things, I'm told that the 2011 Home version will run in Wine.

---

