---
title: "Getting rid of Windows"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by jchristian on 2005-03-17
Howdy folks,

A while back I set up a dual boot system Windows/Ubuntu.  The only reason I kept Windows in the first place was that I didn't have a compatible modem and needed internet access, but now I have an external modem. and am getting rid of Windows for good.
My question is, is there anything special I need to do with my partioning scheme besides getting rid of the Windows partition? My current scheme is:

part 1--Windows

part 2--Ubuntu

part 5-- grub loader

Thanks in advance for any help !

---

### Post by MeasureYouGive on 2005-03-17
what do you mean by "getting rid of the windows partition" - what are you going to do with it?

if you have partition magic you can delete that partition then resize the partition that ubuntu is on to use the new space... otherwise you have to create a new partition (with new file system, ext3 for example) and mount it as whatever you like... 

or you could reformat entirely to rearrange your partitions.  I find it useful to put /home on its own harddisk so that I can keep my data when changing distributions, or reformating the root filesystem for whatever reason.

good luck.

---

### Post by std on 2005-03-17
I agree. Normally, you won't need to do anything special about that partition. You can either reformat it, or delete it and format it, it's your choice. As long as you don't tinker with your other partitions (e.g. merging two partitions using Partition Magic) there's nothing to worry about. I, too, keep my /home on a sepparate partition so that if I need to install another distro or update my current distro or whatever else, I'll have it in a safe place. Of course, you should also remove the Windows entry in grub's OS selection menu, and that's quite about it and change your fstab/mtab settings after you reformat the partition, but that shouldn't be a problem.

---

### Post by mr_ed on 2005-03-17
So in other words, if you don't want that partition anymore, you can do this:

```

$sudo cfdisk /dev/hda

```
Highlight /dev/hda1 (should say either FAT32 or NTFS as a type), and delete it.
Make a new partition and have it fill that space.
Exit.

Then to create a filesystem, type
```
sudo mke2fs -j /dev/hda1
``` for an ext3 partition or
```
sudo mkreiserfs /dev/hda1
``` for a ReiserFS partition

Then you need to assign a mount point to it.  Say you call it /data.

You have to actually create the mount point.
```
sudo mkdir /data
```

Edit /etc/fstab.  Copy your Ubuntu line (/dev/hda2) and paste.
Replace the hda2 with hda1, and change the mount point to /data.

That should be about it, unless Ubuntu doesn't come with all of those utilities, in which case you'd need to apt-get them.

---

### Post by jchristian on 2005-03-20
Thanks guys!
That did it!

---

