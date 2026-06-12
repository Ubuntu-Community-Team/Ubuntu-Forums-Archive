---
title: "Interrupted 12.04 installation at partition selection, now can't even get that far"
date: 2014-05-29
forum: Installation &amp; Upgrades
---

### Post by evilbrent on 2014-05-29
So I admit I got impatient and decided it would be a good idea to turn off the computer after it appeared to hang while deleting a partition. Not actually DOING the partition delete, just I pushed the delete partition button then it went into Deep Thought mode and so I restarted the process. Now it's been thinking for an hour and won't progress beyond the first "preparing to install ubuntu" screen to the list of partitions.

Is there anything I can to do encourage it to move on?

---

### Post by coffeecat on 2014-05-29
I'd suggest no encouragement at all at the moment. It sounds as though there might be a problem with your hard drive. First time around the installer hung while marking a partition for deletion, and now it's hanging while (presumably) trying to scan the drive.

I suggest cancelling the installation wizard. Did you boot straight into installation mode or did you go to the live desktop first? Whichever, it would be best to boot freshly into the live desktop and do some investigations. Post a screenshot of the gparted window. The output of these commands might be useful:

```
sudo fdisk -lu
sudo parted -l
```

Also - open Disk Utility (or whatever it is called in 12.04). Make sure gparted is closed before you do. See what Disk Utility has to say about the SMART status of the HD. Do a SMART test.

---

### Post by evilbrent on 2014-05-29
Thanks, I'll give those a try. 

Strangely it's able to actually boot back up onto the partition that it started to delete, albeit in read-only mode.

---

### Post by ajgreeny on 2014-05-29
If you are in a position to do so, ie, you are not dual booting with lots of non-backed up files you must keep, it may be worth trying to use gparted from a live ubuntu system and go to Device ->Create partition table.

That may repair any damaged partitions, if there are any, and allow you to start again from scratch.

It is still worth using Disk-utility to check the overall health of the disk.

---

### Post by evilbrent on 2014-05-29
Yeah, cactus. The output of fdisk and parted shows the partition tables I was expecting, but running gparted just sits there scanning for partitions. 

Time for a new drive. It's been giving me problems for years anyway. Time to retire it I think. 

Thanks.

---

### Post by evilbrent on 2014-05-29
Ooh. Ok, so I found palimpsest & starts the disk utility (gui of live CD is betraying me) and a few things happened.

Unable to delete partition, check filesystem or format volume "daemon is inhibited". Ran SMART test ok and has some bad answers:

Disk has 1781 bad sectors. "Reallocated sector count" = 346. "Current pending sector count"=1435.

Everything else otherwise labeled "good". Drive has "powered on = 4.1 years" which is kinda old right?

I think it's kerflui.

---

### Post by coffeecat on 2014-05-30
That would be my assumption too. Sorry to hear that.

---

### Post by gordintoronto on 2014-05-30
A drive with bad sectors is garbage, luckily new drives are quite cheap these days.

---

### Post by evilbrent on 2014-05-30
Yeah, new drive got installed yesterday and works like a dream now. (after stupid brent got his head around the concept of not installing a 64bit OS on a 32bit machine! That's 8 hours of my life I'm not getting back)

In fact I'm convinced that the computer is working faster even. I think that I've been reinstalling ubuntu on the regular now for about 3 years and futzing about with read/write errors all over the place from day one, and now my wife thinks that Ubuntu is a terrible operating system, when the truth is probably that we fried the hard drive pretty much on day one because we lived in a place that regularly got to 47C (117F) and left the computer on 24/7. I'm pretty sure that that's been 80% behind almost all of our linux problems from day one.

Thanks all.

---

### Post by gordintoronto on 2014-05-31
And the irony is, today I installed my latest OS on a drive with bad sectors. I will try to DBAN it, and put it in the trash.

---

