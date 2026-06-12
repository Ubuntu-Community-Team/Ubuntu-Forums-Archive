---
title: "partition advice sought..."
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by thegutterpoet on 2010-09-19
I have an external 320gb Hard drive. My plan was to have 250gb for My Documents of mainly music, films and word documents. And 50gb set aside for ubuntu, in a separate partition.

To do this I need to partition the 50gb partition as ext4????
then add a swap file of how big???

please help!

Do i even need a swap space if I have 4gb of physical RAM?

---

### Post by mörgæs on 2010-09-19
Since you have plenty of hard disk space you could give the swap partition 10 GB and use the rest for ext3 or ext4 partitions. 

50 GB for Ubuntu is more than enough. 10-15-ish should be plenty, if you are a regular user.

You can do a live boot and set up all the partitions from Gparted.

I shall not go into the debate of ext3 versus 4. There are lots of threads on that topic.

---

### Post by dino99 on 2010-09-19
swap dont need to exceed 2 Go, set / to max 15 Go, so you get more room for your /home

---

### Post by Alexis Phoenix on 2010-09-19
External swap is going to be slow unless you have firewire or usb3 on your external drive - even then it may still be more of a bottleneck than internal.  If you have super big ram, you may be able to get away with no swap at all.

AFAIK, current Ubuntu uses ext4, but mine is quite happily running on ext3. It should still work with ext2, reiserfs, or any other file system that supports Unix style permissions and attributes, but you will lose out on the ext4 goodness and some things may not work as expected.

I have 11GB set for my / partition, and when I install stuff I sometimes have to uninstall other stuff to make room, so it's not really big enough.  I would think 15GB at least, with hindsight - OTOH, I like to play...

---

### Post by srs5694 on 2010-09-19
You can probably get away without swap space; however, swap space is used for suspend-to-disk operations as well as for actual swapping. Thus, if you intend to use suspend-to-disk, you should definitely create swap space that's at least as large as the RAM you've got. As Alexis says, swap on a USB device is likely to be slow, so if you can resize an internal-disk partition by enough to handle your swap, that's a better solution.

---

### Post by thegutterpoet on 2011-11-04
I am back with the same request for very simplified advice as I prepare to install the new ubuntu...I aim to install it alongside Windows 7.

I ran through to the partition change screen and was shown this:

sda1 ntfs 104.9mb  sda2 ntfs 320.0gb

Device
/dev/sda
/dev/sda1 ntfs 104mb 35mb (used)
/dev/sda2 ntfs 319965mb Unknown (used)

/dev/sdb
/dev/sdb/ntfs 1000202mb  42745mb (used)

I aasume that sdb is my external HD, which I wish to leave alone.

I have most my music, documents, photos and films on the external HD. And save most new documents there...

So...on my 320gb internal HD, I have Windows 7, and that other small partition...

can anyone please advise me how to use the partition tool in the install program to repartition, and also, what sized partitions are advised???

will resizing the windows 7 partition destroy any of windows 7???

---

