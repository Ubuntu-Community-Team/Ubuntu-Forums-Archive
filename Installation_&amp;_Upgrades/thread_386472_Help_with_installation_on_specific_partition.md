---
title: "Help with installation on specific partition"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by oanda on 2007-03-17
Hi all.  I was recommended Ubuntu by a friend, and I really want to install it on my spare partition.  I've allocated about 12 gigs to it, all formatted and ready to go.  But when I go to install Ubuntu, it only asks if I would like to install on top of my main partition or format that partition and install (unless I'm missing an option, which I feel is the case).  It asks me for a swap partition and this and that--all I want is Ubuntu to be installed on my free partition.  How do I get that to work?

---

### Post by Kateikyoushi on 2007-03-17
What kind of partition did you make for ubuntu ? It needs 2 actually one swap, make it 1GB at most, filesystem swap and a bigger one make it ext3 for the system.

If you made fat or ntfs partition then delete it during installation then create the two partitions I recommended.

For more detailed instructions I would recommend to read this page. [LINK]("http://www.psychocats.net/ubuntu/index")

---

### Post by oanda on 2007-03-17
Do you think it would be easier to go back into Windows, merge that partition back so that I have only my one drive, and let Ubuntu do all the partition work for me?

Also, will Ubuntu install a boot loader?

---

### Post by Kateikyoushi on 2007-03-17
It will install the boot loader, and if you leave there and empty space, I mean remove tha partition from windows, it can configure the partitions automatically, but I would rather do myself for learning a bit about partitions, might come handy later.

---

### Post by buuntuu! on 2007-03-17
hi!
have you tried to "manually edit partition table"? it's only a little rickier than the automated install, but you need to be aware of what you are doing. kateikyoushis link is a good place to start.

---

### Post by oanda on 2007-03-17
I have this annoying boot loader from an old version of BeOS that still pops up on boot (and I've deleted BeOS a long time ago).  I know this isn't the right forums, but does anybody know how I might get that to disappear?  I figured it was installed in the BeOS file system, but that is apparently not the case.

---

### Post by Kateikyoushi on 2007-03-17
When you install ubuntu it will be replaced by ubuntu's bootloader grub, or do you want to remove it from windows ?

---

### Post by oanda on 2007-03-17
Well, I merged before the reply was sent, so I think--unless it doesn't work out--I'm going to let Ubuntu do the partitioning for me.  So which install option should I choose?  I now have one partition, the main one, with about 25GB of free space that I want to give 15 of to Ubuntu.

I was thinking of using the "Use largest continuous free space," but that doesn't let me choose how much space to give to Ubuntu on the new partition.  I don't want it to use ALL of the free space it can get.  And the other option, to use part of the free space of my main partition, doesn't let me allocate less than way too much space to the new Ubuntu partition.

---

### Post by Kateikyoushi on 2007-03-17
Choose manual partitioning, and follow the guide I linked before, it is not difficult.
You can make screenshots with the Printscreen button, so if you are really in doubt post them and we will tell what to do.

---

