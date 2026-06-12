---
title: "Partitions and booting"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by Lord Stig on 2010-06-05
I have several linux distros and Windows XP on one hard drive, each in their own partitions. Having filled the drive up I would like to be able to remove a few partitions to keep only one Ubuntu and one XP OS on the drive.

I am not an expert, and reluctant to mess around with GRUB2 config files etc. (I wouldn't know how). I thought I would try booting from live CD, removing a partition and then resizing XP (on sda1) to use some/all of that space.
This didn't work. I wasn't allowed to increase the size of the XP (or any) partition and had 15GB now without a partition. It also messed up GRUB2 since the partitions were renamed for some reason (Lucid was on sda7 but moved to sda5, etc.). So I created that partition again and installed another copy of Lucid there. This is now the default boot option despite me installing StartUp Manager from Ubuntu Software Centre and specifying the right one.

What I would like is to have the option (how??) of resizing sda1 (XP) and sda5 (the copy of Lucid I want to keep) and losing all my other partitions and distros. How can I do this? I don't seem to be able to increase the space allocated to each partition, even when I delete a partition and free up enough space. And it only seems to mess up GRUB anyway. 
I really don't want to have to start again from scratch installing XP and all its updates, etc. and setting up anti-virus, then installing a fresh copy of Lucid.
(I know for Lucid I should have set up a separate home partition, and if anyone can help me with the above problem I will probably do so!)

Many thanks in advance.

---

### Post by darkod on 2010-06-05
In this case to make things easier to understand, can you open the disk in Gparted, make a screenshot and attach it here?

Also, put a few lines explaining which partitions you want gone, and which kept if you know them from looking at Gparted.

One reason for not allowing the extension of /dev/sda1 that I can think of, is if you only deleted logical partition. The extended partition serving as a container for the logical partitions stays the same size after deleting a logical partition, the unallocated space would appear inside the extended, not out of it so you can use it.

Hope that made sense. :)

---

### Post by Lord Stig on 2010-06-05
> **darkod said:**
> In this case to make things easier to understand, can you open the disk in Gparted, make a screenshot and attach it here?

Also, put a few lines explaining which partitions you want gone, and which kept if you know them from looking at Gparted.

One reason for not allowing the extension of /dev/sda1 that I can think of, is if you only deleted logical partition. The extended partition serving as a container for the logical partitions stays the same size after deleting a logical partition, the unallocated space would appear inside the extended, not out of it so you can use it.

Hope that made sense. :)

Thanks. Yeah, it makes sense I think. I know you can only have four primary partitions and so I have XP on a primary partition and all the Linux distros on an extended logical partition - a container for more partitions? The attached screenshot of Disk Utility makes it clearer to me than gparted did.
I only want sda1 and sda5 (plus of course the corresponding swap, whichever that one is). I tried removing a swap before but wasn't allowed to.
It would be nice if I could extend XP's partition by 10GB or so but as you say this might not be possible. In any event I want to extend sda5 and its swap partition to fill whatever space is not used by XP. Grub would also need to boot Lucid by default, not XP.

---

### Post by darkod on 2010-06-05
It's a personal preference. I get a better overview with Gparted. :)
If you notice the partitions list under the graphical layout in Gparted, it will depend if the unallocated space after deleting a partition is under the extended partition (inside it), or outside.

Anyway, if you now have two ubuntus, it makes a difference whether on the MBR you have grub2 from the one you want to keep, or the one you want to delete. As you noticed, deleting the root partition makes a mess sometimes.

I would suggest booting the ubuntu you want to keep, and to make sure its grub2 is on the MBR execute:

sudo grub-install /dev/sda

If the other linux partitions you have on the disk are not included in any auto mounting commands, etc, deleting them shouldn't create any issues with your ubuntu that you want to keep.

Makes sense?

Once you get this far, you will notice whether the unallocated space on the hdd is inside the extended partition or outside of it.
Important note: if the unallocated space is inside the extended partition and you plan to shrink it to get the space out of it, don't boot the hdd ubuntu, instead boot with the ubuntu cd in live mode.
I don't know why, but that still mounts your swap partition so it will have a key symbol next to it in Gparted, and also the extended partition because swap is inside it. That is the thing blocking the resize.
Right-click the swap partition and select Swapoff. That should remove the key symbol from it, and from the extended partition.

After that you can shrink the extended partition to make the unallocated space inside it "go outside". It also depends where the free space will be, at the front or back of the partition, which end you need to "move".

Also make sure you don't over-do it with the shrink (moving the start/end bar. Both root and swap are logical partitions and should stay inside it. You can't shrink the extended partition to a position where root or swap would have a part outside of it.

---

### Post by darkod on 2010-06-05
To add, after you added the Gparted image.

If /dev/sda5 is your ubuntu you want to keep, boot it from grub2, then do the:

sudo grub-install /dev/sda

Then restart with the cd in live mode. Open Gparted and delete /dev/sda7 and /dev/sda8. If any swap file has the key mark, do the swapoff.

According to Gparted deleting those two partitions would leave unallocated space at the front of /dev/sda2, the extended partition.

Don't forget to hit the green Apply button to apply deleting the partitions.

Then click on the left border of /dev/sda2 and drag it to the right, just before /dev/sda5 starts. I think you can literary drag it like that in the graphical layout.
If you are happy how it looks, hit the Apply button and the unallocated space should appear before /dev/sda2, outside of it.
Then you should be able to easily expand /dev/sda1 into it.

After booting your ubuntu from /dev/sda5 again do the:

sudo update-grub

to update the grub.cfg which might contain the ubuntu you added later too, and after that got deleted.

---

### Post by Lord Stig on 2010-06-06
> **darkod said:**
> To add, after you added the Gparted image.

If /dev/sda5 is your ubuntu you want to keep, boot it from grub2, then do the:

sudo grub-install /dev/sda

Then restart with the cd in live mode. Open Gparted and delete /dev/sda7 and /dev/sda8. If any swap file has the key mark, do the swapoff.

According to Gparted deleting those two partitions would leave unallocated space at the front of /dev/sda2, the extended partition.

Don't forget to hit the green Apply button to apply deleting the partitions.

Then click on the left border of /dev/sda2 and drag it to the right, just before /dev/sda5 starts. I think you can literary drag it like that in the graphical layout.
If you are happy how it looks, hit the Apply button and the unallocated space should appear before /dev/sda2, outside of it.
Then you should be able to easily expand /dev/sda1 into it.

After booting your ubuntu from /dev/sda5 again do the:

sudo update-grub

to update the grub.cfg which might contain the ubuntu you added later too, and after that got deleted.

Thanks Darko.
I've done what you said but still haven't been allowed to grow my XP partition (sda1). I can use the 250GB USB hard drive I have for extra Windows storage so it's not too big a problem that sda1 only has 1GB left on it (I may tell Windows to use the USB hard drive for virtual memory if needed).I decided to just extend sda5 (Lucid I wanted to keep) and create a 1GB swap next to it (probably about right as I have 1.5GB RAM).

After I hit apply in Gparted I got two "failed to mount (name of partition). The device is locked" error messages but it carried on resizing. Presumably this was the two partitions I was trying to remove.
I restarted my computer and booted from sda5, then did sudo update-grub and all seems fine!

Thanks very much for all your help - you replied quickly and made it easy to understand. :-) :-D

---

### Post by darkod on 2010-06-06
Sorry, I didn't notice right away, now I know why it didn't want to extend /dev/sda1. If you look at the Gparted image (that's why I like it), there is the warning triangle mark next to it. That means some problem was detected, which might be any small problem, but Gparted doesn't want to touch it as precaution.

If in Gparted you right-click /dev/sda1 and select Check, it might tell you more. I think it will advise you to run chkdsk from XP.

---

