---
title: "Oh noooo!!"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Overthere on 2010-01-14
I'm currently sitting here looking at how to partition by PC. I'm not sure whether to put only Xubuntu or leave half the HD for Kubuntu (already present)..!

If I want ONLY Kubuntu, how do I make partitions???

ANY help GREATLY appreciated!

Brian :confused:

---

### Post by audiomick on 2010-01-14
what do you have at the moment?

could you post the output of
```
sudo fdisk -l
```
that's a small L, not a one.

---

### Post by Overthere on 2010-01-14
audiomick,
thanks for responding..
I've decided to install Xubuntu on the whole disk, and maybe I'll slice it up as soon as I'm finished.. Someone today mentioned using gparted, and I'll install it and see if it will guide me, or if I have to ask you guys more details..!
We'll see...

Brian

---

### Post by audiomick on 2010-01-14
Ok.
you might want to have a look at this.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by SchizmWolf on 2010-01-14
Ahah... don't expect gparted to guide you. 
I recently did the same thing as you're trying to do, and had to spend a while trying to get it to work correctly. My advice is:

1) Delete all current partitions
2) Set up a gig or two for a new partition as "Linux-Swap", and label it "swap"
3) Make another partition about 6-10 gigs of the ext3 filetype, and label it "/" (it'll come in handy on install.)
4) Make one more partition out of the rest of your harddrive space in the ext3 filetype, and label it "/home"
5) now, on install of xubuntu, it'll prompt for guided partitioning or manual. Click manual. then mount the swap to "swap", / to "/", and /home to "/home". Simple as that!

If you've a lot of hdd space and/or RAM, you might want to consider expanding the swap partition, maybe as high as 4 gigs. Same thing with "/", though I don't anticipate you'll need much larger that 10 gB of root formatting space :s

Best of luck!

---

### Post by estyles on 2010-01-14
Assuming that you don't have data that you need to save on the HDD, then I fully support SchizmWolf's advice.  Delete the partitions and make new ones as he specifies (if you do have data that you need to save, obviously don't delete the partitions or you'll lose it all).  I would probably tend toward the high side for size on "/".  If you have plenty of room on your drive, I might even go up to 15GB or 20GB.  Odds are you'll never use that much, but it's a pain to resize drives once they have data on them.

I really don't like the standard advice of "use guided partitioning" - the installer seems to be really bad at deciding how to use your space, and it's really not that hard for a user to create a swap partition, ~10 GB's for system partition, and the rest for /home.

Really, if a new Ubuntu user isn't able to fire up the live CD and use gparted to do that much and then mount them during install, then it doesn't bode well for future use of the OS (unless, of course, you stick to "standard" least-common-denominator use like web browsing with a wired internet connection - but it seems like 90% of users use some sort of non-standard stuff even though they all think it should be completely standard and normal to have a blue-tooth web cam, wireless telepathic joystick, and to be able to install and create programs in gtk with no prior development experience).

---

### Post by Overthere on 2010-01-14
Schismwolf and others,
Thanks for the help!
I am installing the updates for Xubuntu (only OS now on this pc) and when it's done I'll divide them manually. Where do I go to do it? Up to 4gb is fine, I have a total of 160gb on this pc and I want SPEED!

---

### Post by Overthere on 2010-01-14
OK..
Gparted tells me thus:
partition      file system    mount point  size   used                unused                      flags
/dev/sda1  ext4              /                   142.96gb     4.41 GiB (used)   138.55 Gib (unused)  boot
/dev/sda2  extended                          6.09 GiB
   /dev/sda5  linux-swap                     6.09 GiB


Look good or not? Haven't touched anything yet, it was all Xubuntu's work here..

Thanks!
Brian

---

### Post by audiomick on 2010-01-14
Well that will work at least. It is interesting that the install put swap into a logical partition. I didn't know it did that.
You will notice that the swap partition is the same size as the extended partition it is in. If you intend to make more logical partitions, you will have to make the extended partition bigger first.

I would have made a separate partition for /home. This enables you, during a theoretical future re-install, to retain all your data and settings by simply re-mounting /home without formatting. Don't worry about it, just bear it in mind for the future.

If you don't have any really pressing need to change anything, just leave things the way they are. It should work fine.

---

