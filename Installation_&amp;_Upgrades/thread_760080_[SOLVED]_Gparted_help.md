---
title: "[SOLVED] Gparted help"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by eeboy on 2008-04-19
I just set up a dual boot scenario with XP and ubuntu. When I went through the Ubuntu install I let it automatically consume the remainder of the free space on the drive assuming I could adjust it later if I wanted but it appears that is not the case. Is this because the partition is mounted? If so, what's the easiest method to accomplish this? Can I boot from a thumb drive into gparted and fix this?

---

### Post by NightwishFan on 2008-04-19
Boot the Ubuntu live cd and run System -> Administration -> Partition Manager. It is of course gparted. In the live cd all your partitions should be unmounted except swap. Unmount swap if it shares an extended partition with the ones you want to move/resize.

---

### Post by Pumalite on 2008-04-19
Better use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
It works with unmounted drives/partitions.
(one of the reasons it's superior)

---

### Post by NightwishFan on 2008-04-19
Pumalite you have.. an absurd amount of beans. :)

---

### Post by Pumalite on 2008-04-19
Yes. I like to hang around.

---

### Post by eeboy on 2008-04-20
Ok, I resized the ubuntu partition but I am left with a chunk of unallocated space which I wish to use as a share between ubuntu and xp. My partition layout is attached. 

[ATTACH]66491[/ATTACH]

Gparted will allow me to create a new partition with the unallocated space but that partition resides under /dev/sda3 (as a child... not sure what the correct terminology is here). I want it to be a seperate partition. Is that silly or am I just missing something?

Also, what would be the best filesystem for a shared setup? I am thinking NTFS.

---

### Post by forestpixie on 2008-04-20
It will be a seperate partition, but logical instead of primary. A hdd can have 4 primary partitions as a maximum - if one is extended you can have many logical partitions within.

I would go with ntfs myself. Ubuntu will be able to read and write to it.

---

### Post by eeboy on 2008-04-20
Thanks! Are there any negatives to it being logical instead of primary? I would think a primary partition would be better since I could wipe the ubuntu primary partition and retain the shared partition (not sure why or if I'd ever do that but just a thought).

---

### Post by thisiam on 2008-04-20
i would go with ntfs, but make sure you go to synaptic package manager and install NTFS 3g for read and write access.

---

### Post by forestpixie on 2008-04-20
You could do that - you would need to resize the extended to get rid of the unallocated and then make a primary - up to you :) - perhaps it might be worth doing both keep a proportion in the extended unallocated for the future, never know when a partition might come in handy.

When you do all this do each step seperately and apply at each stage - and be aware that it can take some time.

Do not assume that because nothing appears to be happening it's hung - let it finish in it's own time - wouldn't be the first 'I turned gparted off and everything's gone' thread. 

Make sure you have backups of anything you can't afford to lose - although it looks to be fairly empty in there :)

Good luck.

---

### Post by eeboy on 2008-04-20
Thanks forestpixie!

I used the gparted live cd to attempt to resize the extended and it would not let me. The move/resize option is enabled but when it brings up the dialog box the minimum size and maximum size are the same so it won't let me scale it down. My next thought was that I needed to delete the unallocated space from the partition before I scale it down but deleting the unallocated space isn't even presented as an option.

Any suggestions? Seems like this should be pretty simple and straight forward...

---

### Post by forestpixie on 2008-04-20
Mmm... not sure - try moving the swap to the left so that the unallocated space is not between sda5 and 6 and then resizing the extended. You won't be able to delete it as there is nothing to delete as far as I know.

TBH the last few times I've used the gparted livecd it caused me some problems so I've been using something else instead.

---

### Post by eeboy on 2008-04-20
Hmmm... that doesn't work either. I can't reposition the unallocated space. Any other suggestions?

---

### Post by sandysandy on 2008-04-20
from what i can gather sda3 is ur extended drive having sda5 and sda6 as logical volumes inside it.

if u want the unallocated space of 140.53 gb to be formatted to NTFS, u can try to make a new logical partition (which may be sda7)

regards

---

### Post by eeboy on 2008-04-20
Correct... I can create a logical partition but I'd like to create a primary. That's what is proving to be a pain.

---

### Post by sandysandy on 2008-04-20
> **eeboy said:**
> Thanks forestpixie!

I used the gparted live cd to attempt to resize the extended and it would not let me. The move/resize option is enabled but when it brings up the dialog box the minimum size and maximum size are the same so it won't let me scale it down. My next thought was that I needed to delete the unallocated space from the partition before I scale it down but deleting the unallocated space isn't even presented as an option.

Any suggestions? Seems like this should be pretty simple and straight forward...

give it a try again and make sure ur trying to resize sda3.

here is a link to gparted tutorial

[http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

>  Correct... I can create a logical partition but I'd like to create a primary. That's what is proving to be a pain.

any particular reason for primary versus logical:)

some links



[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

regards

---

### Post by eeboy on 2008-04-20
Thanks for the help Sandy!

I tried again and it still will not let me re-size. It does bring up the dialog as if it is going to allow me to but when I attempt to manipulate the size nothing happens. The minimum size is equal to the maximum size and allows no changes. Even if I manually enter the size it reverts back to the current value.

No reason in particular for now. I can use a logical as my share and I should be fine. However, I am thinking in the future I might need to resize the XP partition. If I need to increase its size then I'd be stuck unless I can figure out how to decrease the size of sda3.

---

### Post by sandysandy on 2008-04-20
r u able to resize within the extended drive.

what i mean is r u able to resize sda 5 or sda 6( swap)

regards

---

### Post by eeboy on 2008-04-20
Problem solved...

That was mentioned before but I focused mainly on moving the unallocated space. All I had to do was move the swap forward and that enabled sda3 to be resized. Seems silly but I am sure there is a good reason.

Thanks for your help!

---

### Post by sandysandy on 2008-04-20
welcome:)

---

