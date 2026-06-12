---
title: "removing winxp without reinstalling ubuntu"
date: 2005-06-25
forum: Installation &amp; Upgrades
---

### Post by jasplund on 2005-06-25
I'm planning on removing my winxp since I only have 20 GB on my laptop. I'd be great to do this without having to reinstall ubuntu.

I'm downloading SystemrescueCd right now. I will remove the ntfs partition with qtparted. Also I want the free space to be emerged to my linux partition. Is it possible to do that with qtparted from a liveCD?

What else do I have to do? except removing windows from grub?

yes I will backup everything first, of course I will.

---

### Post by Lunde on 2005-06-25
[QUOTE=jasplund]I'm planning on removing my winxp since I only have 20 GB on my laptop. I'd be great to do this without having to reinstall ubuntu.

I'm downloading SystemrescueCd right now. I will remove the ntfs partition with qtparted. Also I want the free space to be emerged to my linux partition. Is it possible to do that with qtparted from a liveCD?

What else do I have to do? except removing windows from grub?

yes I will backup everything first, of course I will.[/QUOTE]

Why do you want it to be emerged to your linux parttion? is'nt it better to keep the partion, convert it to ReiserFS or Ext3 and mount it as /home.

---

### Post by jasplund on 2005-06-25
well it's only 5 GB and that is too little for /home. Sure I can mount to a folder in /home but it'd be annoying to be knowing that my files in /home are on different partitions

---

### Post by mingus on 2005-06-25
[QUOTE=jasplund]
I'm downloading SystemrescueCd right now. I will remove the ntfs partition with qtparted. Also I want the free space to be emerged to my linux partition. Is it possible to do that with qtparted from a liveCD?
[/QUOTE]

You'll probably not know without just trying.  Sometimes a partition cannot be resized if the space is before it, i.e., you cannot change the partition's start address.  Some partitioners have built-in rules to avoid risks while others do not.  And some have capabilities that others do not.  PartitionMagic is generally considered the best, and even it cannot/will not do some things.

Re QTParted:  It uses the same underlying code (libparted) as GParted and Partman, the partitioner in the Ubuntu install, which I assume you used.  This is important because mixing partitioning tools is dangerous.   If QTParted can't do the job, I'd reconsider leaving this as a separate partition.  I would just mount it to a directory of my naming under /home, then it's transparent.

---

