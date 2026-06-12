---
title: "Holy CRAP! Catastrophe with my system!!!"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by themightymegatron on 2008-10-15
Okay, here's a long story for you. This weekend I was doing by (very irregular) backups. I managed to partimage everything on my external Western Digital 500GB My Book. This is where I actually installed ubuntu, splitting it between 5 partitions. 
> 1.)Primary EXT3 mounted at '/'
2.)Primary EXT3 mounted at '/home'
3.)Logical partition split between:
3a.) Swap
3b.) EXT3 used for backups and extra storage
3c.) NTFS used for my windows XP installed on my internal laptop HDD

Well by sheer "luck" the day after I complete my backups, while ubuntu is running, my cat knocks my external HDD off of the shelf it rests on and to the floor 3 feet below. At first I freaked. It crashed my system, but upon the first few reboots it appeared fine. Then, lo and behold, I booted up so I could start transferring my partimages to disc for safety, and as it's booting it switches to TTY1, spitting errors about not having job control, and several commands missing. I shutdown and booted into a hardy liveCD, hoping to run FSCK, fix whatever, and go from there. After running FSCK on partitions 1, 2, and 3b on the external, it all appears okay, after e2fsck fixed several inode errors in '/'. I reboot from the hard disk and continue to get errors. At this point I decide to just reinstall ubuntu and restore my backups.

So, having a bad feeling, I boot into the livecd again, and run
> sudo e2fsck -fc /dev/sda1  
I can't remember if the -fc had capital letters or not, but I know I ran it right, I just told it to force check and run badblocks to check for bad blocks. After several hours it completes and I have many many bad blocks on the first several cylinders of my HDD. They were all added to the bad blocks inode, and I decide at this point to repartition the first 2 partitions and reinstall. So I do just that, installing the bootloader on /dev/sda1.

Grub spits errors. I change the boot parameters to boot from (hd0,0) and it goes into boot. Then ubuntu spits errors at me.

Repartition and install grub at /dev/sda instead. Change parameters and it boots into ubuntu but now I get a nice little error box about the gnome settings daemon not loading right. "Eh." I think and try to work with it anyways. Immediately since I hardlined my DSL modem to my laptop it tells me I have updates waiting. I tell it to go and it downloads all of them, but when it tries to install them it can't. Reboot & try again, same issue. 

Reinstall AGAIN. grub goes on /dev/sda. Will not boot.

Again. grub on /dev/sda2. No boot.

Again. And again. And again.

Nothing.

Now I've tried to install 3 times today and right as it gets to 94% completion, it locks. I let it sit for 4 hours at one point, came back and it was still at 94%. Grrrr. The live CD is in pristine condition. I cannot find a reason for this to be happening. I even partitioned it to leave the first 10GB of the disk blank as to avoid any bad blocks. Still the same issue. I can't figure it out. Please please please help me!!! *tear drop*

I'm gonna try to reinstall again, and come back into windows when whatever happens happens, and see if I can get anywhere. Thanks so much for any/all help! I just don't get it!

---

