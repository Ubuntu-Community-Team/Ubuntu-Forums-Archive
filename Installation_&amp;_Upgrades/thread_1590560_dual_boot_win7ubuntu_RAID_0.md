---
title: "dual boot win7/ubuntu RAID 0"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by Sharft 6 on 2010-10-08
I'm trying to install ubuntu 10.04 x64 beside my windows 7 but when the setup begins I get this error:

the ext4 file system creation in partition #7 of serial ATA RAID pdc_ecbfebagje (stripe) failed.

Whats wrong?

---

### Post by ronparent on 2010-10-08
You may be working with 10.04 instead of the newer release 10.04.1. In that case the error was that gparted (in the installer) doesn't see the raid partitions and is therefore unable to format them. This is fixable by booting to the live cd, installing a small program called kpartx to the live cd prior to running the install from that session. In step 4 of 7, select the manual partitioning method. Either create or select a raid partition to install to in step 5 of 8. In step 8 of 8, be sure to open the advanced box and elect in a drop down menu to install the grub boot loader to the first raid choice (ie pdc_ecbfebagje). That last step should work, but, if it doesn't, post and I will tell you how to fix so you can boot. Good luck.

---

### Post by lindude on 2010-10-10
Hi Ronparent,
Do you know of a good howto to install ubuntu 64bit in raid 0?
I have tried dual booting 10.04 64bit with a dual boot windows 7 and just using use entire disk. I always got this, (see attached photo), same message. 
Then I tried it same as above dual with windows 7 and using entire disk with 10.10 64bit but grub wouldn't install and after that failed it offered to install grub 2 but that also failed.

I don't want or need windows I just thought it might help because it didn't install form clean HDD's. 

I just bought a new laptop that has two solid state drives which I'd like to use in raid 0. 

I know very little about install ubuntu, I've been using it for a couple of years on my old laptop without any install problems. 

I've been looking around the forms for advice but theres so much to go through, I don't really know where to start. If you have any recommendation that would be great.

Thanks

---

### Post by ronparent on 2010-10-10
lindude - The message is probably because you tried to create a partition without designating the mount point when manually partitioning. Its been a while but in step 5 of eight when you designate your partition to install to, you have to designate / as the file system mount point. See if that fixes you up.

---

### Post by Sharft 6 on 2010-10-11
ok i followed the instructions but I get the same error:
The ext4 file system creation in partition #3 or Serial ATA RAID pdc_ecbfebagje (stripe) failed.

---

### Post by Sharft 6 on 2010-10-27
Should I download ubuntu 10.04.1?

---

### Post by ronparent on 2010-10-27
Another reason for failure is if you already have 4 primary partitions. I usually like to create an extended partition within which I can create essentially any  number of additional partition to meet my needs. If you already have 4 primary partitions, it may take some juggling to get one of those into an extended.

---

### Post by Sharft 6 on 2010-11-05
I just had another go to check I'm not trying to do more than 4 primary partitions but that wasn't the problem. the ubuntu installer just will not format raid partitions.

Here's how I fixed it:
1. start ubuntu live cd
2. install kpartx
[B][U]3. Open up system->administration->gparted
4. do all your partition managing inside gparted[/U][/B]
5. run the ubuntu installer
6. specify partitions manually
7. right click, change the partition you want to install on (**_tick format_**, set the other 2 options)
11. on the last bit of the install click advanced... install boot loader on the top raid option.

---

### Post by ronparent on 2010-11-05
Now the catch 22. You did everything right. But sometimes the grub install doesn't work with the install! Try a grub reinstall - it has always worked for me. See: [https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands](https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands)

Just make sure to mount the raid partition you installed to. And use the name for the overall raid array as the target for the grub-install. If you still have problems, got to: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

Download and run the boot info script found there and post the results here. The initramfs is troubling and we may have to run that down.

---

### Post by Sharft 6 on 2010-11-06
I reinstalled ubuntu again and ticked format the partition this time. dunno if that helped but it works now.

---

### Post by ronparent on 2010-11-07
Probably your best option. Formatting during install is no problem as long as dmraid is installed to the session. 10.10 is better at handling fakeraid during install. Good luck.

---

