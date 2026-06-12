---
title: "monitor turns off when booting with Ubuntu 10.10"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by jchvelasco on 2010-12-25
i can't install ubuntu because after booting from cd. the screen just shows a violet with a man and a keyboard logo on the lower mid and after that the monitor goes off.

---

### Post by Quackers on 2010-12-25
When that screen appears press any key and a new screen will appear. Then press F6 and some options will appear. The most commonly used one seems to be nomodeset. Try that one first and see how it goes. 
If you tell us what your graphics card is somebody may be able to give more specific help.

---

### Post by jchvelasco on 2010-12-25
> **Quackers said:**
> When that screen appears press any key and a new screen will appear. Then press F6 and some options will appear. The most commonly used one seems to be nomodeset. Try that one first and see how it goes. 
If you tell us what your graphics card is somebody may be able to give more specific help.

my graphics card is NVIDIA 9500GT 1gb ddr2. with a driver version of 258.96

---

### Post by Quackers on 2010-12-25
Hmm, if you can't install Ubuntu how do you know the driver number?

---

### Post by jchvelasco on 2010-12-25
> **Quackers said:**
> Hmm, if you can't install Ubuntu how do you know the driver number?

i have windows 7 pre installed.. im going to install ubuntu in another partition

---

### Post by Quackers on 2010-12-26
Ok, try nomodeset then.
Also, as a precaution, you should check how many primary partitions are already in use on your hard drive. 4 is the maximum on any one disc. Don't try to create a 5th or you could get into difficulties.

---

### Post by jchvelasco on 2010-12-26
> **Quackers said:**
> Hmm, if you can't install Ubuntu how do you know the driver number?

how to try nomodeset

---

### Post by jchvelasco on 2010-12-26
> **Quackers said:**
> Ok, try nomodeset then.
Also, as a precaution, you should check how many primary partitions are already in use on your hard drive. 4 is the maximum on any one disc. Don't try to create a 5th or you could get into difficulties.

here's what i get after choosing nomodeset..

unable to find a medium containing a live file system

---

### Post by rabbits on 2010-12-26
Here is a thread about "nomodeset" but it appears you have gone past that point now.  [http://ubuntuforums.org/showthread.php?t=1613132&highlight=nomodeset](http://ubuntuforums.org/showthread.php?t=1613132&highlight=nomodeset)

The "live file system" is your LiveCD.  Have you verified the CD (checksum)? During boot-up of the CD, there should be a checkdisk utility as one of the options.  Have you also tried to make a USB bootup key instead of the CD ie. boot from USB key?

ps: if you try to install drivers and update s/w while running "Live" you will not be able to save the files on a CD.

In my case, I am able to boot from "Live" USB key; with nvidia 6150 integrated graphics and successfully complete the installation.  The nvidia proprietary driver will be loaded after installation and re-boot from hdd. After reboot from hdd, run >System>Admin>Additional Drivers. I did not use "command-line" or any other extra utilities.

Good luck.

---

### Post by Quackers on 2010-12-26
If it's not finding a live file system I would agree with checking the cd for errors.

---

