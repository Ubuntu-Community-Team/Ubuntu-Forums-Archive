---
title: "Growing /boot with gparted"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by Tlanuwa on 2008-03-04
Apologies if this has already been answered, but I couldn't find it!

My problem is this -- I'm trying to upgrade from Edgy ALLLL the way (in increments, of course) to Gutsy. Using the upgrade manager, it's erroring out because my /boot partition is too small (didn't plan for upgrading, etc. as I should).

My swap is far too large, so I wanted to shrink it a bit and give the extra to /boot (the first partition on the drive). I've burned and successfully loaded a gparted CD, but can't seem to figure out a way to take free space at the end of the drive and tack it on to the boot partition at the beginning.

Is it even possible? Is there another solution I might try? I just need 10 more megabytes free on /boot! (I've already deleted old kernels and such...)

Thanks for the help!

- John

Edit: I also have PLENTY of space on my root mounted partition -- can I just move everything from /boot to the root partition?

---

### Post by logos34 on 2008-03-04
> can't seem to figure out a way to take free space at the end of the drive and tack it on to the boot partition at the beginning.

can't do that.

If you have gparted v.3.3 or better you can resize the left boundary of the partition after/adjacent to /boot.  I assume it's root.  But it does take a while--even if you're just trying to grab a few MBs--because it has to copy and move overt everything to the right.

Yes, you can transfer /boot back to root.  Just [follow this]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition") but reverse the process:

---

### Post by Tlanuwa on 2008-03-04
I appreciate the help.

I was actually just about to come over here and post -- it seems it helps if you actually READ the documentation for the software you mean to use.... :-D

The example for moving/resizing in the gparted docs mirror nearly exactly the setup of my system -- I shrank the (almost never even accessed!) NTFS partition by a few hundred MB, shifted all of it to the right, then grew the /boot partition (immediately preceding the NTFS) to fill the space. I DO wish I had realized just how long it would take, but it is, thankfully, about finished (I think).

Even knowing that I COULD have moved /boot to the root partition, I'm happier in the end -- I prefer (don't really know why) having it separate (and at the very beginning of the drive).

Thanks again for the advice though!

- John

---

### Post by logos34 on 2008-03-04
oh, so it's an ntfs partition.

Is it a bootable windows partition?  Because if it is you may need to run error checking (chkdsk /r) on it before you can boot back into it.

---

### Post by Tlanuwa on 2008-03-04
Originally, I wasn't going to touch the NTFS partition, but yes, I have now.

GRUB is installed and working -- will I still need to run chkdsk /r before I can boot? Thanks again for the help!

- J

---

### Post by logos34 on 2008-03-04
actually it may run automatically when you try to boot into windows (dual boot, right?--hope I understand you).  If not then you can run it from the recovery console on a windows install cd

---

### Post by Tlanuwa on 2008-03-04
Yep yep, it's dual-boot (only have Windows for the .Net contract work!) -- here's hoping it all still works.

Thanks again,
-J

Edit: Woot! gparted has finished working its magic. XP is automatically running CHKDSK (which the doc for gparted recommended allowing to complete) -- looks like I'll be good to go!

---

