---
title: "Radeon Issues."
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by krye97 on 2012-04-06
Currently I have access to NO Linux distrobution on my computer, and I am running Windows 7.

My computer has an AMD A8 processor, with Radeon HD 6600M Graphics card.  It's got 8 gigabytes of RAM, so I think lack of processing power is not my issue.

What seems to be the problem is drivers, because when I boot to the disk, it displays the boot picture for about 4-8 seconds, then displays the usual Linux loading screen (the flashing underscore), but does not display any text.  After about 2-3 seconds the entire screen goes black (no backlight at all), but the CD drive makes sounds as if it's loading.

I imagine it's an issue with the drivers that come preinstalled on the disk.  My question is, are there any specific instructions anyone can provide which have been proven to work in similar or the same environment?  If you have any questions about my situation, please ask them, however remember that I am unable to execute any Linux commands unless they come before the LiveCD goes into graphical mode.

Thank you very much,
krye97

---

### Post by darkod on 2012-04-07
Did you try the sticky with video issues which is on top of the threads?

Try few fixes in live mode first, once you know what is the correct fix that worked, you know what to do.

---

### Post by Mark Phelps on 2012-04-07
You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space. When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by krye97 on 2012-04-07
Again I am completely incapable of even seeing any of the utilities required to install Ubuntu!  I boot to the disk, then the screen goes black.

---

### Post by darkod on 2012-04-07
Again, did you read carefully the sticky about the video issues? It has parameters to use to avoid the screen going black.

There are procedures to do during the boot of the cd, immediately, which can help it boot all the way with your video card (hopefully).

Did you try the fixes explained there? You don't need to load live mode all the way for that, that's the point, to use parameters that will help it boot all the way...

---

### Post by darkod on 2012-04-07
Try this:
1. As soon as the cd starts booting and the first purple screen is shown (before the language menu), hit Esc. That should bring up the boot menu of the older type.
2. Leave the Try Ubuntu option highlighted and hit 'e' for edit. That will open the boot lines.
3. Position the cursor on the line starting with linux, after the text 'quiet splash' and add 'radeon.modeset=1'.
4. Press Ctrl + X to boot.

See if that can manage to boot working live mode.

---

