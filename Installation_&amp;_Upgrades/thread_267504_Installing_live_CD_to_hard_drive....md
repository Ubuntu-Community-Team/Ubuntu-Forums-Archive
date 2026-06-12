---
title: "Installing live CD to hard drive..."
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2006-09-28
OK, I have tried the live CD, and I like what i see. Particularly after my last windows crash! (If only it turned out to be the last one...)

I have used partition magic to make a new EXT3 partition, for Ubuntu to live in.

But I can't work out how to get transfer the live CD to the HD, so I have a dual boot system! It seems a rather fundamental option, so I am probably missing something obvious here...

The other OS is Windows XP.

Any clues or pointers woul be very gratefully received.
Thanks,
Nick

---

### Post by Kateikyoushi on 2006-09-28
Well you can click the install icon on the desktop to start the installation which is quite straightforward.
You have to repartition your hard drive if you did not made a swap partition.

---

### Post by hatalyl on 2006-09-28
i don't have it in front of me so.. i would do it something like 

click the install icon on your desktop.
follow the step. (keyboard, timezone, username,etc..)
when you get to partitioning/formatting your harddrive (step 5 from memory), choose "manually edit the partition table"
choose the partition that you formatted to ext3 and remove it, create 2 new partitions, 
the first will be a SWAP partition 1 to 2 times the amount of ram you have, so if you have 512 Mb ram make it 512mb - 1024mb)
the second will be a / (root) partition, the rest of the space minimun of 3GB in size.

the / partition will need to be a primary partition. i also make the SWAP partition a primary partition but i don't think i need too, i think in a default install it is actually an extended partition, .

click ok/next

***** make sure that you windows partition (will usually be hda1 but depends on you setup) is **NOT **marked to be formatted. *****

when you have the option to install GRUB it should detect winXP for you if not don't install it to the mbr.

click ok/next and let it do it's thing.

you will have to say ok to a few things along the way, but as i said this is all from memory so i cant give exact instruction.

hatalyl

---

### Post by starbase1 on 2006-09-29
I can't see an install icn on my desktop!

There are the available drives as icons near the top left, and a strip above it with applications, then places then system, but nothing I can spot as an install icon...

Where should it be?

Nick

---

### Post by Kateikyoushi on 2006-09-29
Should be on the desktop where your drives are.
I can not recall exactly but I think when you boot from cd then you can choose install, I might be wrong...

---

### Post by starbase1 on 2006-09-29
Thanks - it's not there. I have left the machine at home downloading the latest disk image - I am using one from a few moths ago at the moment, so it's probably wise to get the latest one any way.

Nick

---

### Post by Kateikyoushi on 2006-09-29
Sure but download version 6.06 and not 6.1 which is beta few people reported complications during the install.

---

### Post by unisol on 2006-09-29
0n the live cd go to system/preferences or system/adminstration and look for the install program or you could boot into safe graphics mode and do a text install

---

### Post by orb9220 on 2006-09-29
these are latest dapper iso's 6.06.1 lts [http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)

As stated above do not use the 6.10 edgy as that is still buggy, Just tired it myself and it is.

---

### Post by starbase1 on 2006-09-29
Thanks to everyone for your help - I am seriously impressed with the level of helpful responses I heave received to such a basic question. 

:D :D :D 

I am hoping that the new disk will produce an install icon for me to click on!

:cool: 

Nick

---

### Post by starbase1 on 2006-09-30
OK! It took a bit more effort than I expected, but I now have a dual boot system.

I downloaded the latest ISO image, and sure enough, that one had an install icon.

The Ubuntu stuff could not resize the c: partition - from windows I found there was an unmovable file fragment near the end of the disk. I used partition magic to shrink the partition, forcing it to move that segment, and freeing up some completely unallocated space at the end.

I was held up when it decided to do a full disk check, (2 hours!), but then I let the ubuntu installer find it, and everything went smoothly.

I was very nervous, but it's coming along beautifully.

Now to go and start a new thread with my next question!
;) 

Thanks for the encouragement here guys!
Nick

---

