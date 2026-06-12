---
title: "Snapfile swap error on startup"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by maxvenus on 2008-11-03
Hi all

so i installed Ubuntu 8.10 on the same partition as my vista, i have installed previous versions of ubuntu and suse on this computer many times, but recently i have this error when booting Ubuntu..

*checking local filesystems
 fsck 1.41.3 [12-OCT-2008]           [OK]

  *mounting local filesystems...     [OK]
  *activating swapfile swap... 

and it will then sit there, if there is anyone who can help please do let me know as i would love to get back on linux :)

thanks guys

---

### Post by carljmoss on 2008-11-04
Same problem here. I installed Intrepid to coexist with XP on an NTFS drive, using wubi. It doesn't actually hang at '*activating swapfile swap' - it takes 10 or more minutes to complete! After that it seems to load normally. I've checked with swapon that the swap file is activated - it seems to be - and there are no worrying messages when I examine the output of dmesg.

In fact, when installing Intrepid, ubiquity took a very long time to make the swapfile.

I've not renamed or altered the swapfile in any way.

I had Hardy in place before this and everything was fine. I've tried upgrading from Hardy and doing a clean install from the Intrepid CD. I get the same problem both ways.

---

### Post by maxvenus on 2008-11-04
any ideas on how we could fix this then?

I just dont understand... maybe i will make new partition just for ubunt, and see if we have any luck there, i will keep you updated :)

---

### Post by carljmoss on 2008-11-04
I tried creating a new swapfile inside Kubuntu, deactivating the old one and then using the new one in its place. This was booted much faster.

So, my guess is that when the swapfile gets created on the NTFS drive it is fragmented. I'm going to defrag the disk under Windows and then reinstall Intrepid and see how it runs. The swapfile will be pretty large and the chance of NTFS keeping it contiguous I'd say is pretty low on a fairly full disk.

I've moved my iTunes database to a different drive to free up a lot of space. It's defragging at the moment. I'll post my results back.

If you do make a new partition for Ubuntu I'd guess you won't see the slow boot: the new partition will be ext2 or ext3, and these don't suffer from fragmentation like FAT32 or NTFS do.

---

### Post by carljmoss on 2008-11-05
Well, defragging the NTFS disk and clearing away some space seems to have helped. There's still a noticeable delay activating the swapfile - although this time it's measured in seconds, not minutes.

This still looks to me like like an unfortunate feature, if not a bug, of the Intrepid release.

---

### Post by maxvenus on 2008-11-05
man im still waiting for my HD to defrag, its a 1TB, so its going to take a while man :( 

i will sure let you know how it works, but why dont you install Ubunt on a new partition, im sure it will solve the problem. I will inform you on how ubuntu boots as soon as i have completed the instalation of ubuntu ;)

---

### Post by maxvenus on 2008-11-19
i have got linux fully running on the harddrive, i just wiped windows **** off and installed SUSE and Ubuntu =D working great and im loving it

---

