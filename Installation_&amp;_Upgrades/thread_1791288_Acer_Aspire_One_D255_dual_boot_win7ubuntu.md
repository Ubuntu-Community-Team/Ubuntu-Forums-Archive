---
title: "Acer Aspire One D255 dual boot win7/ubuntu"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by Biggetje on 2011-06-26
Dear ubuntu community,

I recently bought a netbook, the Acer Aspire One D255.
It boots android 2.1 and win7 starter, but I don't want android. I want ubuntu.

There is one 250 GB HDD. there are four partitions, one 'C:', one 4GB for Android downloads (which I have formatted a few times, but it keeps going back to that), one recovery partition and one 100mb.

How do I get rid of android to install ubuntu?
I tried to merge the 4GB with a part taken from the C volume, but it seems I can't do that.

I am in need of your assistance!

---

### Post by foresthill on 2011-06-26
Have you tested out the live CD version yet, to make sure your netbook will run Ubuntu without problems? I would suggest you install 10.10 if you do install, due to the number of bugs that still need to be worked out with 11.04.

Also, do you have some kind of recovery media in case you make a mistake? If not I would just keep Android where it is for now, to be on the safe side.

What I did on my Win 7 notebook was go to Disc Management, and there is an option there to create a new partition from the free space on the disc. So I created a new partition in Windows and installed Ubuntu there.

I am not familiar at all with Android OS, so keep that in mind, but if you do what I did, you should be OK, AFAIK.

---

### Post by Biggetje on 2011-06-26
I tried 11.04 using a boot-USB (no cd-drive). It started up, but I haven't really used it for anything. It was just a test.

I can ofcourse Shrink the C volume and use the new partition to install ubuntu, but I will still have this leftover 4 GB 'android downloads'. 

All the recovery software is on the recovery partition. 
I assume I could simply format everything and then reinstall windows 7 starter & enter the key that came with the laptop.

---

### Post by lhowaf on 2011-06-26
You could download gparted and Universal USB Installer to create a bootable gparted. Then use gparted to shrink, move and/or delete partitions. After that, you can let the Ubuntu installer figure out the partition configuration for dual bott win7/ubuntu.
I did this on a D255 - except I did it on a separate drive so I could fail back to the original if necessary.

---

### Post by Mark Phelps on 2011-06-28
Do NOT use Gparted to mess with any of the Win7 partitions.  Doing so is asking for trouble.  Instead, use the Win7 Disk Management utility to shrink and/or remove the partitions -- to make room for Ubuntu.

Let the Ubuntu installer do the Linux filesystem formatting.

---

### Post by Biggetje on 2011-06-29
I made a partition by shrinking the C partition.
I've installed Ubuntu on that one.
However, I'm still stuck with this 4GB space, what shall I do with that?

---

### Post by Biggetje on 2011-06-30
I'd like to know how I change the boot priority with ubuntu.
When I turn on the power, I get to choose between ubuntu or win7. If I don't press anything It'll start ubuntu. How do I change that to win7?

---

### Post by foresthill on 2011-06-30
With regard to the 4gb partition, I'm guessing that now you have Ubuntu and Windows 7 successfully dual booting you could just format it, either in Windows or in Ubuntu, and use it for storage or whatever.

With regard to the boot order, you can install the program Startup Manager, from the Ubuntu Software Center applet, or from Synaptic Package Manager. 

This will give you options on which OS you want to boot as default. And you can also edit you boot menu too, I believe. This might come in handy after you format the 4gb Android partition. You'll be able to delete that entry from the boot menu.

---

