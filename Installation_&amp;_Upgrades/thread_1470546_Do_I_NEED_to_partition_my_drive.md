---
title: "Do I NEED to partition my drive?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by hedgeborn on 2010-05-02
Real simple question. I just completed a clean install of Lucid Lynx netbook version on my netbook and realized I did it all in one big partition using Gpart

Now, I'm a newbie (obviously) but I am reading all sorts of things telling me I should have a "swap" partition and a home partition and so forth.

I'm confused as to how to start over and do it the right way, how/what to name the partitions and if any of this is even necessary.

The computer is working fine. I understand the benefit of having a seperate /home partition etc but I am clueless as to how to set these partitions up in Gpart, how big they should be and how the installer is going to know where to put what.

Any guidance would be appreciated. Thanks

---

### Post by hedgeborn on 2010-05-03
bump

---

### Post by hedgeborn on 2010-05-03
Anyone out there?

---

### Post by Genius314 on 2010-05-03
It depends.

Swap I believe is necessary on notebooks and netbooks, as this is where your RAM is stored when the notebook goes into hibernation/sleep mode. Most people suggest making the swap partition about 1.5 to 2 times the size of your RAM. So if you have 2 GB of memory, your swap partition should be about 3-4 GB.

Having a /home partition is completely optional. I love it, because it allows you to do a clean install without needing to backup your files (although I still recommend it).
Generally I give the root partition (the one Ubuntu is installed on) about 10 GB, maybe a bit more if you plan on installing a *lot* of extra programs. The rest of the drive can be given to the /home partition.


You can do the partitioning right in the installation process.
BACKUP YOUR /HOME FOLDER FIRST, ONTO A SEPARATE HARD DRIVE (or two, if you're feeling extra paranoid. :P)
(*this is assuming you actually have stuff in your /home folder. If your home folder just has the default stuff in it, there's probably no need to backup)

1. Basically, when you get to the step in the installation process asking where to install Ubuntu, choose the very last option (it should say "specify partitions manually" or something like that)

2. Click "forward." You should come to a screen with a partition tree. Since you said you don't have any partitions, you should probably only see one drive, /dev/sda or something like that, and one partition listed under that drive, /dev/sda1.

3. Select the partition, right click, and delete it. Now there should just be one item in the list, something like "unallocated space."

4. Right click on the unallocated space, and select "new partition." Set the size to about 10'000 MB, the mount point to /, and the filesystem type to ext4 (or ext3, if you want). I think the "format partition" box should already be ticked - if not, do so. Click Okay.

5. Do the same thing as step 4, but... where it asks for the size, there should already be a value there. Figure out how much you will need for swap (1.5 to 2 times your RAM), and subtract that from the number in the box. Set the mount point to /home.

6. Make yet another partition. It's size should default to whatever is left, which should be the amount you calculated in step 5. Set the partition type to "swap". Click okay.

7. Click "forward," and continue with the installation.

NOTE: If any of the above doesn't make sense, ask before attempting to do this. You can always click "Quit" if you're not sure of something, and nothing on the hard drive will be changed. I typed all of this up from memory, so I'm not too sure if some of the terms are correct.

---

### Post by steveneddy on 2010-05-03
It is not necessary to partition.

If your install is running fine I would leave it alone.

Don't fix what isn't broken.

---

### Post by shortpaw on 2010-05-04
Hi, hedgeborn
   I'm a relative "newbie" as well, and I may simply be confusing the issue. That said, when I have installed Ubuntu (and Mint) from the live CD, I've always chosen the "Use entire disk" option for both my Acer & Asus netbooks (both with 160GB HDDs).
   If I check "Disk Utility" in "administration", and look at "volumes" on my hard disk, the graph indicates that the install created a 3GB swap partition by default.
   I'm not familiar with the partitioning utility that you used for your install, but I'd take a look at Disk Utility; you may have nothing to be concerned about at all.
   I hope this is of some help.

---

