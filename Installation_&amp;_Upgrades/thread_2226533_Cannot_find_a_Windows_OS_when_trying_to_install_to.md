---
title: "Cannot find a Windows OS when trying to install to dual boot with Win 7"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by jeff67 on 2014-05-27
Hello,

My Win 7 Pro is here, as that's what I'm using to write this, but I'd really like to use Ubuntu for everything except gaming.

When I made the DVD, during the I believe 3rd screen of installation, it went to what seemed to be a partitioning screen and after saying it could find no current OS.

I just did a clean install of Win 7 Pro from a retail DVD and have 800mb + free on a 1 TB drive that I just saw on that partitioning screen, so I know it sees there is data there. 

I've dual booted before with other computers and had no problems.

I've seen other peoples questions on here, but I couldn't find one of a clean install of Win 7 that had this problem. 

Thank you for your help.:KS

---

### Post by fantab on 2014-05-27
Tell us more about your machine's hardware like, RAM, CPU and Graphics etc.
Does your machine use UEFI or the outdated BIOS?

Boot with Ubuntu DVD/USB and 'Try Ubuntu (without installing)'. After desktop loads open Terminal [ctrl+alt+T], run the following commands and post its output here:

```
sudo parted -l
sudo fdisk -l
```

This will tell us how Linux sees the partitions.

Also post the screenshot of your HDD and its partitions using Windows Disk Management tool...

---

### Post by jeff67 on 2014-05-27
AMD FX-8320 
ATI R9 270
1600mhz 2x2gb crucial  

Pic of disk management attached. 

Doing the boot from DVD thing now. 

Thank you for replying!

---

### Post by jeff67 on 2014-05-27
Shoot, I'm downloading updates for this new copy of windows, I'll do this as soon as I've restarted and I'll restart again to make sure it's all installed before I do this even though it probably doesn't matter.

---

