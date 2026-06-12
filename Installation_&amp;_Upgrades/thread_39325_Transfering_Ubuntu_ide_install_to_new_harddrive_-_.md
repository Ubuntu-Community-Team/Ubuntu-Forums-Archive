---
title: "Transfering Ubuntu ide install to new harddrive - SATA partition"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by op3studios on 2005-06-04
Hello, 
I like Ubuntu so much I want to copy my program and add-ons, like an image, to an existing free partition on my SATA (currently running only XP).
I'll be dumping XP to my ide soon!
Is there a way to transfer my ide Ubuntu install to another harddrive?
Drive image seem a bit extreme since my home directory on my Ubuntu ide is very large.  Larger than my SATA space.
I just want to transfer the Ubuntu program set up as I have it now, with a resized home partition, so I don't have to do all the updates config etc all over again, and have my changes and updates intact on the new drive/partition.
What's the best way to do this please?
my ide Ubuntu partitions = root, home, FAT32(don't need to transfer FAT)


Mist rising sunlight
Sparkling comes the newday.
Here now;  Ubuntu.

---

### Post by Dogmeat on 2005-06-04
Well i did something like this yesterday, I moved the ubuntu install into my larger HD. I had to resize the ntfs partition (defrag, and used ntfsprogs), deleted the ntfs partition and created a new, resized one, with fdisk. Then I created a ext3 partition on the remaining free space, used parted's cp to copy my whole ubuntu root partition, and edited menu.lst in /boot/grub to reflect the new install (I must still change something in grub, I can boot fine but had to remove every savedefault or I get a error 15 in grub)

Be sure to have some livecd lying around just in case something goes wrong. I used RIP (Recovery Is Possible), works great  :grin: 

Please feel free to ask about any details that aren't clear enough!

---

### Post by mingus on 2005-06-04
[QUOTE=op3studios]Hello, 
I like Ubuntu so much I want to copy my program and add-ons, like an image, to an existing free partition on my SATA (currently running only XP).
I'll be dumping XP to my ide soon!
Is there a way to transfer my ide Ubuntu install to another harddrive?
Drive image seem a bit extreme since my home directory on my Ubuntu ide is very large.  Larger than my SATA space.
I just want to transfer the Ubuntu program set up as I have it now, with a resized home partition, so I don't have to do all the updates config etc all over again, and have my changes and updates intact on the new drive/partition.
What's the best way to do this please?
my ide Ubuntu partitions = root, home, FAT32(don't need to transfer FAT)[/QUOTE]

There are a number of ways to go about this.  Here is one from SuSE, which can be adapted.  I have used it successfully.  Extreme care to understand what is being done and exec precisely.   A big plus is the ability to test the copied system without disturbing what was copied, and to do this from your current production system.  I also install grub to floppy first, do not want to touch the mbr until I am sure I have the new boot config correct.

[http://houghi.org/user/apb.html](http://houghi.org/user/apb.html)

---

