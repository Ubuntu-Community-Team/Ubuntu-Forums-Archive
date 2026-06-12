---
title: "Ubuntu installed on small partition, now I'd like to increase it and relegate Vista"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by quarryman007 on 2008-08-23
Hi all, first post.

So I installed Ubuntu and have just about got it working to the way I like (well for everything except games).

It has 12 GBs (out of 160) to itself. I'd like to increase that now and take the unused space from the windows partition.

What's the best (safest) way to do this?

thanks in advance.

---

### Post by nautikal on 2008-08-23
You can use a windows program like Partition Magic.

---

### Post by Patb on 2008-08-23
Quarryman, you might be best to set up a separate home partition if you don't already have one. To give you a fuller answer, could you let us know the partition setup you have. Please post the output of 
```
sudo fdisk -l
```
Cheers, Pat

---

### Post by quarryman007 on 2008-08-23
hey pat,

here ya go:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15       17829   143093750    7  HPFS/NTFS
/dev/sda3           17830       19457    13076910    5  Extended
/dev/sda5           17830       19382    12474441   83  Linux
/dev/sda6           19383       19457      602406   82  Linux swap / Solaris

---

### Post by stinger30au on 2008-08-23
i always thought the easiest thing to do was to install windows and drivers on the hdd first and let it have its way your pc fist, and then install ubuntu

---

### Post by quarryman007 on 2008-08-23
> **stinger30au said:**
> i always thought the easiest thing to do was to install windows and drivers on the hdd first and let it have its way your pc fist, and then install ubuntu


yep, that's what i did. Now I'd like to enlarge the ubuntu partition.

---

### Post by rabidg00se on 2008-08-23
This isn't a complete solution to your problems, but it should get you most of the way there, albeit you'll lose access to your swap partition. If you can figure out how to restore that, this will work. (The problem is, Vista installs onto two partitions at the front of the disk, then Ubuntu's swap, then Ubuntu itself, meaning that the eventual free space and the actual Ubuntu partition will be noncontiguous. The only way I've found to fix this is to delete swap and recreate it.)

First, of course, back up everything of importance.

Then, in Vista, right-click on Computer. Go to "Manage," and in the left pane of that select "Disk Management." Right click on on the "OS" partition, pick "resize" or whatever the option is, and decrease it by the amount that you want to add to Ubuntu. That should all now be free space or unallocated or something similar, and highlighted in green.

Now, download the GParted Live CD (just Google GParted), and boot from it. Now here's the part that's given me trouble. My solution was to simply delete the swap partition, making the Ubuntu partition and the free space contiguous. From there you can easily resize the Ubuntu partition to fill the free space. The problem is, if you then recreate swap after the new Ubuntu partition, Ubuntu doesn't use it and I don't know why. If you can find a way around that (or have enough RAM to not care about swap), this method should work for you. If you have a solution, please post it--I'd love to hear it.

---

### Post by Partyboi2 on 2008-08-23
Maybe another possible method is to do as mentioned above
> Then, in Vista, right-click on Computer. Go to "Manage," and in the left pane of that select "Disk Management." Right click on on the "OS" partition, pick "resize" or whatever the option is, and decrease it by the amount that you want to add to Ubuntu. That should all now be free space or unallocated or something similar, and highlighted in greenThen use gparted live cd or gparted on a ubuntu live cd (System>Admin>Partition Editor) then turn off swap (highlight, right click, swap off) then move (resize) everything to the left to take up the unallocated space. (This can take along time) Then turn swap back on after finishing.

Edit: Forgot to mention when working on partitions make sure they are unmounted (right click, unmount) first as you will not be able to work on them while they are mounted.

---

### Post by rabidg00se on 2008-08-23
Oh my God...you can just...*turn it on!* Thanks!

---

