---
title: "server, sata, pata confusion on install"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by redshirt99 on 2008-05-27
Perhaps my foray into ubuntu will be very short :)

Trying to install ubuntu server edition 8.04 on a Dell Dimension 2350, P4 w/ 30 GB pata HD.

Once in the partition screen it detects the pata drive as sata/scsi sda. It errors on an attempt to install to the 24.7 GB of free space stating that it is "Probably too small" .

1. Are all drives in linux sda by default now? I thought this would be hda or similar.

2. Shouldn't it know if it is too small? Too small isn't a probably  condition.

Searched and found reports of not finding a drive but not of finding and mistaking type like this. Anyone else see this or see it resolved?

-r

---

### Post by dstew on 2008-05-27
All drives are given sda designations now, I don't know the significance of that. Whether PATA, SATA, or SCSI, they all come out sda.

That is a strange error message. I have never heard of it before. Certainly 24.7 GB is not "too small" for any Ubuntu installation. Can you post a screenshot of this message so we can see it in context?

---

### Post by redshirt99 on 2008-05-28
Some more info... this has Win XP Pro in the primary partition. I am asking it to partition and install in the free space (assuming it will make a 2nd primary, install there and install its own dual boot boot loader).

It errors for all approaches to installation to this free space.

I'm gonna try the desktop version.

-r

---

### Post by dstew on 2008-05-28
Maybe what you are seeing is that your Windows partition has 24.7 GB of unused space. That space is not available to make a new partition until you shrink the Windows partition. Did you try to shrink (menu item Resize) the Windows partition yet?

---

### Post by redshirt99 on 2008-05-28
Hmmm... for a minute I was hoping you were right. Nope, it errors... with only "An error occurred while writing the partition information to the disk."

Oh well.

---

### Post by dstew on 2008-05-28
The server install is a text-based interface, correct? If so, it might not have the capacity to resize, only delete or create new partitions out of unallocated space. Also, sizes are in megabytes, so 10 GB is 10000 MB.

To resize, you would have to use something like [gparted]("http://gparted.sourceforge.net/livecd.php").

---

### Post by aaron.d on 2008-05-28
So im confused. Is this a full partition or some other chunk of "unallocated" space?

If so, this should work fine. Try getting the default 8.04 live cd and grab the output of 
```
sudo fdisk -l
```

or even try running gparted.

---

### Post by redshirt99 on 2008-05-30
I tried it on another WinXP system with a FAT32 drive. Same problem. Also, same problem when I tried it with the desktop version with GUI. It simply does not want to resize the existing windows partition.

So I gave up on that approach. I hunted down some older even dustier hardware in the back, cleaned it up and installed over windoze.

It worked fine for that.

All drives involved were pata.

-r

---

