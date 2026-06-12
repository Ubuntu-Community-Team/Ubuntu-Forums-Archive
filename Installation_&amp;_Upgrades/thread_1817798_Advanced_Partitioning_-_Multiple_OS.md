---
title: "Advanced Partitioning - Multiple OS"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by dodle on 2011-08-03
I want to install multiple Linux OS's on my system with a dedicated GRUB partition. I have been trying to research how to do this. I'll explain how I plan on doing this, but I need some feedback. If something that I am doing isn't a good idea please let me know.

Here is what I imagine my partition table to look like:
```
/dev/sda1 | ext2 | /boot/grub (primary partition)
/dev/sda2 | swap (logical partition)
/dev/sda3 | ext4 | / (logical partition for multiple OS)
/dev/sda4 | ext4 | /home (primary partition to be shared on multiple OS)
```

So here are a few questions: I read that it is okay to put swap on a logical partition, is that correct? Am I doing the correct thing by making /dev/sda3 a logical partition for installing multiple OS's:

/dev/sda3 (20000MB):
```
10000MB for root Ubuntu install
10000MB for root Debian install
```

And is it okay to share /home over multiple Linux installs?

---

### Post by YesWeCan on 2011-08-03
Each linux OS needs a separate partition.

A swap partition may be logical

Your /home is probably not shareable among different OS's because config files may be different in different versions of apps in different OSs. I haven't thought this through but my instinct would be to keep the default /home in each OS file system but have a shared ext4 partition.

So I would probably arrange it like this:

sda1 grub
sda2 extended
sda5 swap
sda6 shared ext4 partition
sda7 linux OS #1
sda8 linux OS #2
sda9 linux OS #3
...

That's the easy part. The trickier part is setting up the grub partition. The way grub installs by default is that it is grafted on to a linux OS. To separate the Grub files from an OS and put them in their own partition requires some manual crafting. You will also lose the ability to run update-grub so each time you add an OS will require a manual edit of grub.cfg.

See: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by dodle on 2011-08-03
That is some excellent information. Thank you YesWeCan.

About the multiple OS's. My understanding is that a hard drive can only have a certain number of primary partitions. So I thought that logical partitions could be used to create more partitions. Am I wrong in thinking that you can put multiple OS's partitions under one logical partition. I guess this would only be important if one were install 4+ OS's on one disk. Is it a bad idea to put that many OS's on one disk?

---

### Post by YesWeCan on 2011-08-03
> **dodle said:**
> That is some excellent information. Thank you YesWeCan.Pleasure. :)

> About the multiple OS's. My understanding is that a hard drive can only have a certain number of primary partitions. So I thought that logical partitions could be used to create more partitions. Am I wrong in thinking that you can put multiple OS's partitions under one logical partition. I guess this would only be important if one were install 4+ OS's on one disk. Is it a bad idea to put that many OS's on one disk?
Yes, but I think your terminology is a little off. You can put multiple logical partitions under/inside an extended primary partition. You can only have one extended primary partition. You can have as many logical partitions as you like because they are daisy-chained.

Windows can only be installed to a primary. So it is nice to keep one or two free in case you ever want to install Windows. Now that I think about it, your Grub partition could be logical too IF you are intending to install Grub's boot program to the MBR (which is how Grub is usually configured). In this case you only need 1 extended primary partition, leaving 3 unused primary slots.

Many ways to skin a cat. Hope this helps.

---

### Post by dodle on 2011-08-03
You have been a great help. Thank you very much. And thanks for clearing up how partitions work.

---

