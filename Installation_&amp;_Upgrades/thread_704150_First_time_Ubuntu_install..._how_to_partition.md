---
title: "First time Ubuntu install... how to partition?"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by miamisubs on 2008-02-22
Hi, after a bit of research I have a pretty good idea of what to shoot for but not exactly how to get there.  I am looking to install and dual-boot Ubuntu on a Vista desktop with a 250GB hard drive, about half of which is currently occupied by data.  My understanding is that the following would be a good method of repartitioning the drive:

#1 - modest Vista partition (NTFS)... not sure how many GB
#2 - modest Ubuntu partition (ext3)... maybe 10 GB?
#3 - large shared partition for media and other files (ext3)
#4 - swap partition (1 or 2 GB?)

I was looking at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) (which is where I'm getting the divisions above) and it recommends putting /home on the larger shared partition to allow for carefree installs down the road, but I have no idea how to set up a "/home + shared" partition as opposed to putting /home on the same one as Ubuntu itself.

Can anyone advice me on whether this plan is a good one for my purposes, and if so then specifically how to go about partitioning things?  I've looked at the Ubuntu Live CD's partitioner (though not pulled the trigger on anything yet) and also checked out the full version of GParted, although that didn't seem to boot correctly for me.  I can sort of see how you designate partition sizes and file formats, but I am paranoid about losing a bunch of existing data in the transition and I don't really understand the "/dev/hda1" structure type headings.  Also, does the actual order of partitions in the list matter?  As in, should the shared partition be "in between" the two OS partitions, or is that inconsequential?

Anyway, let me stop here before rambling further.  Thanks for any advice!

---

### Post by agim on 2008-02-22
Welcome to Ubuntu. What I did, until I became acclimated enough to mess with partitions, was to create a small partition from within Vista. I think it is safest to let Vista itself do this. Then I booted the livecd and told it to install on largest continuous free space. The installer will make sure you have a /root partition and a swap partition. A /home partition can be added later if you still want it.

Good luck!

---

### Post by agim on 2008-02-22
Also, a shared partition isn't entirely necessary since Ubuntu can write to your Vista partition. 7.10 has this ability installed by default.

---

### Post by miamisubs on 2008-02-22
Ah, thanks for the heads up.  Vista's defragmenter is running now -- the shrink utility only discovered a small bit of possible space before (like 25 MB), so hopefully that will improve after the defrag.  I'll forget the extra partition for now and just let the Ubuntu installer do its thing with the contiguous space.

I'll probably be bumping this once I get things get moving again.  Thanks!

---

### Post by zvacet on 2008-02-22
>  A /home partition can be added later if you still want it.

Why doing same job twice?Make separate home now.You will find more confusing do it later.

---

### Post by Bucky Ball on 2008-02-22
Welcome to the learning curve! I agree with zvaset. Something to remember though. Even though Ubuntu might see your NTFS and Windows partitions, this will not work the other way around. If you are in Windows, your ext3 partitions are invisible, even though you can see the physical drive in your Windows 'Disk Management' page, you can not access or manipulate the data on the ext3 partitions from within Windows.

Common to have a fat (16 or 32) partition for data swapping between OS's - both Linux and Windows can deal with this (not sure if there is any other file system they are both 100% happy with). I have an external drive formatted with FAT32 I use for this purpose occasionally.

Happy to stand corrected here by wiser heads - if there is a better way, bring it on. Good luck with it all.

---

