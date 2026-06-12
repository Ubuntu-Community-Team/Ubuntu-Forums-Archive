---
title: "GRUB after reinstalling Vista"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by ettorelars on 2010-03-31
Hi all! as many others before me I installed ubuntu on my HP notebook (with Vista preinstalled) just "to give it a try" in a 10 gb partition. Of course now I'm a happy ubuntu user and would like to reinstall Vista in a very limited partition just for some applications. My question: if I format the Vista partition (to reinstall Vista in a smaller one) will GRUB still see it? Or do I have to reinstall GRUB as well?
Thanks

---

### Post by ajgreeny on 2010-03-31
Unfortunately, reinstalling windows will simply overwrite the grub boot-loader that ubuntu put onto your disk.

However don't get too upset about it, as it is quite easy to restore grub and with grub2 now being used, it is also easy to get grub to find and add windows to the menu automatically.

But do you really need to reinstall windows Vista?  You could always shrink the vista partition using the vista disk management software in safe mode, after a couple of defrags, and with virtual memory turned off, for the best effect.  After doing that check that windows will still boot OK, and then using gparted on the live ubuntu CD you can enlarge your ubuntu partition, by dragging its left border back into the free space.

A few warnings must be sounded about this, of course.  You must make sure all your files are backed up, just in case the worst happens.  Also you should be aware that enlarging your ubuntu partition may take a very, very long time, as you are in effect moving everything backwards on the disk, and that is a slow job;  it does work, I know because I've done it myself.

Also be aware that you may find it difficult to shrink your windows partition as much as you might want, and if that really is the case, ie that you can't make the ubuntu partition as large as you want, then a reinstallation of windows may be the way to go, though in that case you will either have to reinstall ubuntu to get grub back, or just carry on using the same ubuntu install after restoring grub, but using the free space as a new partition, perhaps NTFS shared between the two OSs, or as a defined new /home partition for ubuntu only, ext4 format.

For more info on a separate /home after installing ubuntu see here.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by quinntar on 2010-03-31
Well you can try this CD --> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
It will allow you to restore your grub config in order to find back your linux. Normally it installs the path to windows too.

Quinntar

---

### Post by ettorelars on 2010-03-31
I supposed I had to recover grub, and I'm a bit scared of it as I heard a lot of people being troubled. Of course I can reinstall both Vista and ubuntu.. About shrinking the win partition it could be the best solution to use that free space to create a new  partition shared with vista. But I know there are some limits to shrinking. How about it?

---

### Post by Mark Phelps on 2010-03-31
> **ettorelars said:**
> I supposed I had to recover grub, and I'm a bit scared of it as I heard a lot of people being troubled. Of course I can reinstall both Vista and ubuntu.. About shrinking the win partition it could be the best solution to use that free space to create a new  partition shared with vista. But I know there are some limits to shrinking. How about it?

If you're going to shrink the Vista OS partition, be sure to use the Vista Disk Management utility to do that.  Do NOT use the Ubuntun installer -- doing so runs the risk of corrupting your Vista OS partition and rendering it unbootable.

---

