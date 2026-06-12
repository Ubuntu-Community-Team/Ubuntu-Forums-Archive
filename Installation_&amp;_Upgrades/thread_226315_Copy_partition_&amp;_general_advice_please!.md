---
title: "Copy partition &amp; general advice please!"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by timka1 on 2006-07-31
I have installed Ubuntu on a new 250 GB Samsung Spinpoint hard drive which I bought for its quietness (it is). It was pretty easy but before I get into it I want to have my old XP environment as alternative boot.

What I would like to do is reconnect the old (noisy) drive temporarily and, rather than reinstall XP and reinstall all the stuff the way I had it, I wondered if I can copy the XP partition to a new partition on the Samsung?

My plan is to start from scratch on the new drive and do as follows:

Use Ubuntu installer to partition 

40GB for XP (FAT32)
60GB for Ubuntu (EXT3)
148GB for shared files (FAT32)
2GB Swap

I would then install Ubuntu.

Then use XP Install disk to reformat first partition as NTFS.

Next start up the Ubuntu partitioner where I noticed there is an option to copy data from another partition. However I can't find any posts on this option. Could I use this to copy the old XP partition to the XP partition on the new disk?

I would then disconnect the old drive and keep for occasional use...

Well this is where the questions start!

1) Does this stand a chance of working?

2) No doubt the XP environment will need tweaking because it will not like being moved to a new environment. Is this what the FIXMBR & FIXBOOT commands are for? Or do I have to edit a system file?

Any help greatly appreciated! Or if this is a non-starter let me know as well!

---

