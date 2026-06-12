---
title: "Advice - Extend new system partion on new harddrive"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by paulbuk on 2011-10-08
After successfully cloning the old IDE 80Gb drive to a new SATA 500Gb (and then removal of the old 80Gb), I noticed with GParted that I currently have some circa 389Gb 'unallocated', (I can quite easily sort this kind of thing out having done it many times with M$) but don't really want to trash my MBR or GRUB.

My new system partition has 89Gb which I'm sure is well sufficient for the system/swap file etc, and could quite easily just make a new partition with the 389Gb but me thinks I'd rather have a one 'large' partition.
(FYI, my 'home' is already set on the second 500Gb (both SATA drives are the same model, so I'm not really bothered).
I am currently upskilling in LAMP/Drupal WebDev and work a lot on localhost for playing on WebDev etc and I'm sure 89Gb is well enough for many many SQL D/B's.

If GParted is not the best approach, can someone advise on the safest, quickest route to 'merge' the 89Gb with the unallocated 389Gb into one partition without destroying my MBR or Grub on the current 89Gb.

I'm keen to hear your advice on partition layout or best practice.

Failing the above, I am prepared simply to create a new partition, but I like to keep all my drives 'whole as one' so to speak.

I've attached a GParted png for you to view and I'm sure the opinions will help others in future make positive decisions.

Thanks again.
(:

Paul B, Lancs.

---

### Post by westie457 on 2011-10-08
Hi this is relatively simple and not too time consuming.

First boot into a LiveCD in TRY mode and start Gparted.

Next in Gparted unmount all partitions.

Select the swap and move it all the way to the right. Click the Resize/Move to accept then Apply and Okay. Wait for this to finish.

Do the same with the extended partition.

Finally drag the right hand edge of your main partition to the right as far as it will go. Doing the necessary clicks.

All should be okay. Any problems post back here with any error messages.

---

### Post by paulbuk on 2011-10-08
Cheers, had a feeling it would be something like that, but not wishing to 'trash' the system, held fire.
Will do this afternoon and report back on actions for others to read.
Peace.
(-:

PB

---

### Post by westie457 on 2011-10-08
No worries. It should work flawlessly.
Here is a link to a slightly more complicated one I did. [http://ubuntuforums.org/showthread.php?t=1798827](http://ubuntuforums.org/showthread.php?t=1798827)
Screen shots have been removed.

---

### Post by paulbuk on 2011-10-08
Thanks Westie457.
FYI, my 'home' is on a 2nd WD 500gb, the system is a new one replaced 2 weeks past to replace the old small 80gb as I upgraded my Ubuntu box with a new faster MoBo/Pro/4g RAM/2nd WD 500gb.
I'll maybe move the 'home' later to the new primary HD.

I read your thread, so I'll feedback and compliment later on my results.
(-:

PB, West Lancs. (that place between Liverpool & Wigan)

---

### Post by paulbuk on 2011-10-09
Westie457,
Didn't have much luck with this after bootin with LiveCD and Gparted. Gparted loaded fine, but partions wouldn't move (and I turned off 'Swaps' with the option in the Gparted menu).
I presume I just 'click and drag', if so, it wasn't letting me drag either left nor right.
As per my original screenshot, the unused space is 'unallocated', personally don't think this is the issue. Any ideas? or maybe I've missed a small point.
Cheers

PB

---

### Post by oldfred on 2011-10-09
You have to enlarge extended partition first. Then you will be able to move swap to the right. I would not make very large / partition but create data partition(s).

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

