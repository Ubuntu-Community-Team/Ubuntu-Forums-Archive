---
title: "Reinstalling grub"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by LostShootingStar on 2006-09-24
In my quest to extend the size of my Ubuntu partition (now that i love it) iv come across a problem. here is a summary of what im trying to do.

1. i reduced the size of my windows partition
2. because gparted cant move the start of the ubuntu partition, i made a COPY of it, and pasted it in the unallocated space left from my windows partition. so now i have the same ubunutu installation on /dev/sda2 and /dev/sda4. 

```

/dev/sda: [  windows sda1  | new ubuntu sda4 |==unaloc.=|  original ubuntu sda2 | swap ]

```

thats a diagram of what my partitions look like right now. what i would eventually like to do, is be able to boot the NEW unbuntu partition /dev/sda4 , and then DELETE the original ubuntu installation, and finally enlarge the new ubuntu partition to the end of the drive. 

so my question is...how to I get grub to do this? im really lost on how grub works, and i dont want to end up not being able to boot either of the partitions.

also, will this affect my swap partiton, (e.g. making it unusable, or causing a boot up problem?)

thanks in advance!


edit: here is my fdisk -l output incase it helps

```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2778    22314253+   7  HPFS/NTFS
/dev/sda2            4074        4827     6056505   83  Linux
/dev/sda3            4828        4864      297202+   5  Extended
/dev/sda4            2779        3533     6064537+  83  Linux
/dev/sda5            4828        4864      297171   82  Linux swap / Solaris

```

---

### Post by confused57 on 2006-09-24
You could try to boot the Ubuntu on sda4, by highlighting the Ubuntu entry in grub at bootup...then press "e" to edit, change the root to (hd0,3), and in the kernel line root=/dev/sda4 and see if it will boot.
   If it does boot and you delete the Ubuntu on sda2, it might change the partition # of the Ubuntu on sda4...I don't really know.
You could always boot up with the gparted live cd and determine what your partition tables are after you make changes:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

or you could boot up with the live cd & fdisk -l.

I'm not experienced enough with partitioning to give you any specific advice, but you can see if your sda4 Ubuntu will boot I mentioned above...this editing is not permanent, so any changes will be temporary.

---

### Post by Herman on 2006-09-25
> because gparted cant move the start of the ubuntu partition Have you checked up on that lately? Because I think [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") *can move the start of Linux partitions now*, since version 0.3-1 came out, which has already been superceded by version 0.3.1-1
You can read about version 0.3-1 [here]("http://sourceforge.net/project/shownotes.php?release_id=445059&group_id=115843").
So you should be able to delete your NEW Ubuntu partition and enlarge the old one.

It is still a good idea to have a second copy of your partition to use a  spare in case your working copy gets 'hosed' somehow, I recommend it.

If you still want to continue with your current plan, it will work alright,
confused57's advice on Grub sounds really cool !  :D Once you have booted it your could re-install grub from that operating system to MBR and you would also need to edit /etc/fstab with the right partition numbers to make your NEW Ubuntu system function normally. (because it was installed as /dev/sda2, but now it's /dev/sda4, but you have to tell it so by editing it's /etc/fstab file). It is a well established practice to do things that way. :D

I can now confirm the Gparted LiveCD 0.3-1 definitely can move ext3 partitions, because while I was typing this, I was testing it in my other computer and I moved my dsl partition (ext3), my spare copy of my experimental Ubuntu install (ext3), my experimental Ubuntu install (ext3), and my swap area. I shrunk my extended partition. Then I resized my main (working) Ubuntu install to a much larger size. (I'm a slow typer, all this work was done in maybe around half an hour or so, I wasn't timing accurately though). 
Both of my Ubuntu installs have booted up okay, as I expected.

I recommend GParted LiveCD 0.3-1 or later, GParted's new full 'move' support is great! :D

Regards, Herman :D

---

### Post by LostShootingStar on 2006-09-25
Thanks for the reply. I was using the gparted that comes with the daper live CD, which cant move ext3. i wish i would have seen your post sooner and i would have used a gparted live CD and saved some trouble. oh welll!

anyway, i got this working last night without to much trouble. everything worked fine when i told grub to use /dev/sda4 and (hd0,3). but when i deleted /dev/sda2, grub had "error 22". so after a few min of fiddling i realized that /dev/sda2 no longer existed in the partition table, and that was confusing grub.

I noticed in gparted that when i was copy/pasting the partition, it would alternate between /dev/sda2 and /dev/sda4. so all i did was copy and paste the partition twice, to get sda2 to start where the windows partition ended. then i deleted /sda4 all together, and extended /sda2 and everything works great! a bit of a round about way I guess, but now i know for next time.

---

### Post by Herman on 2006-09-25
> Thanks for the reply. I was using the gparted that comes with the daper live CD Oh, I see. There's nothing wrong with doing that. You did a good job solving your problem, that's the way I used to do it too, just paste the partition again to get the old partition number back again. It seems simple to me, and obviously now to you too. You would be amazed at the number of people I tried to explain that idea to and they couldn't 'get it' or said it was 'complicated'.
 The speed these developers are improving open source software is hard to keep up with. I'll bet there are lots of people who weren't aware of how much GParted has improved since the last Ubuntu release. 
All the best, regards, Herman :D

---

