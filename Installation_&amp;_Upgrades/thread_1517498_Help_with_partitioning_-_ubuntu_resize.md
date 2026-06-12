---
title: "Help with partitioning - ubuntu resize"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by RebeccaB37 on 2010-06-25
Hi guys,

I really need some advice about removing a previous install of Ubuntu (which is no longer serviceable) and reallocating the drive space to my new shiny install of 10.04.

I had a dual boot system (with Vista) and severely messed up my newly-upgraded 10.04 so it could only boot in low graphics (ext3). Because I couldn't find a fix (oldfreds help came just a little after [http://ubuntuforums.org/showthread.php?t=1516777](http://ubuntuforums.org/showthread.php?t=1516777)) and I desperately needed Ubuntu back up and running asap, I reinstalled Ubuntu creating a new partition (ext4) in the process (to preserve Vista) but of course couldn't overwrite my earlier Ubuntu install.

Ideally I want to reallocate the first linux install space to the working partition as I have lost 65Gig of space through my mess up. My g parted screen shot attached shows the set up.

Lots of the forum posts regard reallocating windows / ubuntu space but I can't find discussion of the type of reallocation I want to attempt. My main questions are can anyone offer any advice and how can I check whether GRUB will still load from ext4 when it was originally installed on ext3?

Bear with me - I'm a relative noob who has got into serious trouble over the last two days with my OS any advice most gratefully received!

thanks in anticipation!
Rebecca

---

### Post by kalistona on 2010-06-25
you do not need advice but only erase the old and install the new.
in xp/vista you must follow a special tutorial for dual-boot.
you can also erase a partition and format it, then re-alloued at any os you want. 
nota bene : xp is not vista
extc3 is default and ext4 is new, so you do not need to know that, it is automatic/formating. (sorry for my little poor english).

---

### Post by mikewhatever on 2010-06-25
It looks like the current Ubuntu partition is sda8 and the old one is sda6. There shouldn't be any problem with deleting sda6 and then expanding sda8 into the newly unallocated space. The important this is to do it from the Live cd.
You also seem to have two rather large swap partitions, which you might want to get rid of.

---

### Post by lechien73 on 2010-06-25
From your 10.04 installation on the ext4 partition, I would run:

```
sudo fdisk -l /dev/sda
```

to confirm which swap space your new installation is using.

Then I would boot from a GParted LiveCD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Removing the old ext3 and swap partitions and expanding your ext4 partition into it. Alternatively, you might like to just delete the old ext3 partition, create a new ext4 in its place, and then move your new /home folder to its own partition:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by RebeccaB37 on 2010-06-25
Many thanks for your super fast responses!

Mike - Thank you for your comment regarding the swap partitions, I'm not sure exactly what size of swap partition is necessary - any tips?

Matt - The output of sudo fdisk -l /dev/sda is as follows:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      208813+  de  Dell Utility
/dev/sda2              27        1332    10485760    7  HPFS/NTFS
/dev/sda3   *        1332        5316    31999023+   7  HPFS/NTFS
/dev/sda4            5317       30402   201496575+   f  W95 Ext'd (LBA)
/dev/sda5           30075       30402     2620416   dd  Unknown
/dev/sda6            5317       13842    68481224   83  Linux
/dev/sda7           29067       30074     8096728+  82  Linux swap / Solaris
/dev/sda8           13842       28443   117277696   83  Linux
/dev/sda9           28443       29066     5010432   82  Linux swap / Solaris

presumably this means that sda9 swap is associated with the working install sda8?

Can I be certain that grub will still work having removed sda 6 & 7 as these were my original Ubuntu partitions (or, forgive my ignorance) does it get installed each time you split the drive during install?) Is there a simple check I can run before making any changes?

As for the seperate partition for home, technically I suppose my home folders are still in tact on sda 6? Perhaps I should just leave them there and mount to it / use it for backup storage? Will the (possibly?) corrupted OS affect the stability of this partition for such use?

Sorry for all the questions - if I'd have be brave enough to ask a few more yesterday I might not have got myself in this mess... :)

---

### Post by lechien73 on 2010-06-25
Grub uses the UUID of the partition, rather than a "hard" path to /dev/sdxX

IIRC, resizing a partition *will* change the UUID, which means that your resized Ubuntu will no longer boot. To get around this, either:

a) Boot into your working 10.04, and issue the following command:

```
sudo blkid
```

Note down the UUID of your current ext4 partition. Then reboot using the GParted LiveCD and resize the partition. If - when ;) - Ubuntu fails to boot, then startup from a LiveCD, mount your root partition and issue the sudo blkid command again.

Then change references to the old UUID to the new UUID in /etc/fstab on the root partition, then run:

```
sudo update-grub
```

b) Don't resize the partition, but reformat the old ext3 partition and use it for /home

---

### Post by oldfred on 2010-06-25
I agree with the above posts on reusing the space.

If you have a lot of settings and data in the old install you can copy that to your newest install. You then can delete sda6 & 7 and create new /home or just make it a data partition. I do not recommend moving a system installs start. It can be done but you have to rewrite all the data and it then is very slow.

If the old install did not work you must have installed grub with the new install, so you are booting thru the new install. If it sees the old install it may still be listed in your grub menu. After deleted the old you can run sudo update-grub to eliminate it from the menu.

Swap should be 2GB or slightly larger than RAM if you want to hibernate. When RAM was only 256MB the recommendation was 2 times RAM. With RAM now usually much larger swap is rarely used. Some with 4GB or more say they do not use swap at all but if you happen to load a lot or very large application swap may be used.

You can confirm which swap is used by looking at fstab and comparing UUID with list from.
```
sudo blkid
```

---

### Post by mikewhatever on 2010-06-25
Swap depends on the amount of RAM, but for a relatively modern computer (2-3 years old), 1GB is a safe bet.
Removing partitions is safe as you now use the GRUB from sda8, however, you may have a problem with partition numbering after deleting sda6 and sda7. Keep that live cd ready if Ubuntu doesn't boot, and we'll correct things in a few minutes.

---

### Post by RebeccaB37 on 2010-06-27
Thank you so much to all who responded to my questions, I'm sorry I haven't had chance to reply earlier - I have been away this weekend.

Given all the really helpful advice above, I'm sure I can work this out this coming week.

Cheers!
Rebecca

---

### Post by mk631219 on 2011-03-13
Hi everyone,
I am having trouble with my computer. I accidentally deleted my python and turned off my computer. Right now I am using an old version of ubuntu (ubuntu 8.4) and would like to know how I can restore the python for my ubuntu 10.10 so that I will not lose the things that I have installed on it if this is possible.
mk631219

---

