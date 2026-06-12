---
title: "Can't install lubuntu"
date: 2016-06-23
forum: Installation &amp; Upgrades
---

### Post by loledd_ on 2016-06-23
Hi guys, today i tried to install ubuntu but it failed cause of some I/O errors & ext4 filesystem ( i don't remember ) 
so i decided to install lubuntu (16.05), downloaded the x64 ISO then burned it in a DVD-R with Windows 7's burner.

I had ubuntu before but it had some problems: Skype crashed cause of an 'Input/Output error' and everything stopped working so i rebooted and it kept starting with BusyBox.
Around 1-2 hours later grub won't start, i tried restoring it from the Live CD, yes, it worked but after 2-3 reboots it stopped working again.

The lubuntu installer gets stuck at 'Preparing'.
Searching on the internet i found that it's a partition problem, so i started GParted but it keeps scanning.

I tried to format with Disks but it gave me an error:
```
Error creating file system: Command-line `parted --script "/dev/sda" mktable msdos' exited with
 non-zero exit status 1: Error: Input/output error during read on /dev/sdaError: Input/output error during write on /dev/sda(udisks-error-quark, 0)
```

I think it's an HD problem.
Anyway i have 9048 bad sectors (growing) but disks says 'Disk is OK'.

Oh, sorry for grammatical errors, i'm Italian.

Help appreciated...
thanks :\

---

### Post by Impavidus on 2016-06-23
I don't know why it says "Disk is OK" (maybe the disks utility didn't run a full check?), but to me it seems that that hard drive is definitely not OK.

---

### Post by loledd_ on 2016-06-23
> **Impavidus said:**
> I don't know why it says "Disk is OK" (maybe the disks utility didn't run a full check?), but to me it seems that that hard drive is definitely not OK.

Okay, Saturday I will go to a 'PC Repair' to see if my HD is dead, if yes i will buy a new one there.
Thank you for your reply!

[IMG]http://www.holeboards.eu/images/spinner.gif[/IMG]

---

### Post by mörgæs on 2016-06-25
I agree that the disk has problems.

If you don't plan to store anything important on the disk you could also run Gparted from a live boot and create an empty partition of (for example) 10 GB at the beginning of the disk, hoping that the errors are here only. The partition should not be used. After this create the normal Buntu partitions and install here.

---

