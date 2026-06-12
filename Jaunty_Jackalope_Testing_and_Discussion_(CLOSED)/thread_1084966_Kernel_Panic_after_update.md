---
title: "Kernel Panic after update"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gmclachl on 2009-03-02
Hi,
    I just done an update, which included glibc, anyway I rebooted and am getting a kernel panic, saying that it is unable to read/mount root file system.  If I drop into grub and select 2.6.28-7 then it boots ok, so not sure what has caused the problem. The version I have the kernel panic with is 2.6.28-8

George

---

### Post by gmclachl on 2009-03-03
Sorry to bump this, but am I the only one who experienced this. 

The error I get it is 

[0.179554] ACPI:  Aborted because invalid compressed file
[ 0.735861] cpufreq: No NForce2 chipset.
[3.967767] RAMDISK: ran out of compressed data.
[3.967826] invalid compressed format (err=1)
[3.996184] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown wn-block(0,0)

When running 2.6.28-8, but it boots fine when runing 2.6.28-7

I also have a lot of space on my /boot partition so I don't think that is the issue.

---

### Post by Kow on 2009-03-03
Try reinstalling the 2.6.28-8 kernel. Looks like your initramfs image is corrupt. I think dpkg-reconfigure linux-image-<the rest here> rebuilds the initramfs image.

---

### Post by gmclachl on 2009-03-03
Yeah, I am afraid I tried that, but no luck. Thanks for the suggestion.

George

---

### Post by gmclachl on 2009-03-03
Scratch that. Even though my boot partition was showing up at only 20% usage as soon as I deleted some of the older kernels and reconfigured it, it worked. 

I don't know if ext4 is causing issues with the disk utility tools, although I highly doubt it.

---

### Post by Kow on 2009-03-03
Yea I always show details when installing kernel upgrades. Sometimes "disk full" messages go unnoticed when installing a new kernel version.

---

### Post by keep-on-smiling on 2009-03-04
> **gmclachl said:**
> Scratch that. Even though my boot partition was showing up at only 20% usage as soon as I deleted some of the older kernels and reconfigured it, it worked. 

I don't know if ext4 is causing issues with the disk utility tools, although I highly doubt it.

Yeah, I had exactly the same experience - from a virtually fresh install using ext4. Installed 2 days before, added a couple apps that I consider important (dvdrip, sound juicer, geany, audacity and nvidia driver), removed ekiga, did updates on first day - all fine. Did updates on second day and boom ! Kernel panic ! I have to say I have not seen this in Ubuntu before, through several versions that I have tried out/used.

I had a look at the amount of kernels - just the one so doubt that is the issue. Might possibly be the ext4 file system - think I should try to mount /boot on ext3 in future !!

Cheers

---

