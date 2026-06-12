---
title: "Have RAID 1, can I wipe, dual boot install and keep it?"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by kat3c on 2010-02-24
I'm all set to wipe my Vista 32 bit, partition the drive and install Windows 7 Pro 64 bit and Karmic 64 bit in a dual boot.  But then it occurred to me I have a RAID 1 array, and didn't know if that would be a problem.  So, does anybody know/have experience, will it?  I guess I have 2 questions:

1)  Can I wipe it by partitionng with gparted, do the installations and the RAID 1 configuration is just automatically kept?

2)  If not, then how would I reconfigure a RAID afterwards?  If I can't just easily keep the RAID 1, I might actually prefer to break it and reconfigure to RAID 0.  Do Dual Boot installs work on that kind of array?  Does Ubuntu play well with RAIDs?

Any help and other advice would be much appreciated.  Thanks.

My setup:  Dell XPS 420, quad core Q6700, 4 GB DDR2 800, RAID 1 320 GB HDD, Dell 0TP406 motherboard with X38 chipset and Intel ICH9R southbridge, Intel ICH8R/9R SATA RAID controller.

---

### Post by rickbeton on 2010-02-25
Hi

I'm not able to help directly - but I am attempting a very similar thing. So far without success. But in case it helps here's my story so far...

I have installed Win7 on one disk. I decided to keep things simple: my Windows disk is non-RAID; also I gave it a 500M partition that I can use for /boot.  I bought two new identical disks for Ubuntu9.10.

Using the 9.10 Desktop CD, I ran Palimpsest and GParted. On each of the new disks, I created two partitions as "Linux Raid Autodetect" partitions (this can be done with Palimpsest or with cfdisk). Then I used mdadm to set up my two raid arrays (one raid-0 and the other raid-1). ([more info here]("http://ubuntuforums.org/showthread.php?t=408461"))

Then I installed Ubuntu from the CD onto one of my new raid arrays.  So far so good.

However, when I reboot the PC, grub is incorrectly configured, it has forgotten that the raids exist (although the drives still contain the data), and everything fails horribly at the first hurdle (even Windows doesn't boot now! But that's because the grub config is broken, not Windows)

So this evening I'll do a bit more research on what happens at boot up and why my raid arrays are not found and booted up correctly.

If it succeeds, I'll post a bit more here.
Rick

---

### Post by kat3c on 2010-02-25
Well, I done did it, and it went smoothly. I did decide to get rid of the RAID array, so before anything I went into the BIOS and set the two disks to non-RAID. On rebooting, I just had two exact copies of my drive, both bootable, no loss of data. I then booted to a live Gparted CD, and first repartitioned the first drive for the Windows 7 install (primary partition), with an extended for partitions for data, and an Ubuntu install {4 logical partitions, ntfs, ext4 (linux root), linux-swap, and ext4 (linux home)}. After that finished, without exiting Gparted, I reformatted the second drive as a single NTFS primary partition for additional data storage.

THEN, I rebooted to the Windows 7 DVD, and installed, took 15 minutes. Rebooted immediately to my Ubuntu USB install drive, and that took about 10 minutes, and done! Except for reinstalling programs/setup now and playing. No apparent issues so far, not with the install anyway. Some programs reinstalling are being a pain, like iTunes made two copies of every song file, but that'll give me something to do for the next couple of days.

---

### Post by darkod on 2010-02-25
> **rickbeton said:**
> Hi

I'm not able to help directly - but I am attempting a very similar thing. So far without success. But in case it helps here's my story so far...

I have installed Win7 on one disk. I decided to keep things simple: my Windows disk is non-RAID; also I gave it a 500M partition that I can use for /boot.  I bought two new identical disks for Ubuntu9.10.

Using the 9.10 Desktop CD, I ran Palimpsest and GParted. On each of the new disks, I created two partitions as "Linux Raid Autodetect" partitions (this can be done with Palimpsest or with cfdisk). Then I used mdadm to set up my two raid arrays (one raid-0 and the other raid-1). ([more info here]("http://ubuntuforums.org/showthread.php?t=408461"))

Then I installed Ubuntu from the CD onto one of my new raid arrays.  So far so good.

However, when I reboot the PC, grub is incorrectly configured, it has forgotten that the raids exist (although the drives still contain the data), and everything fails horribly at the first hurdle (even Windows doesn't boot now! But that's because the grub config is broken, not Windows)

So this evening I'll do a bit more research on what happens at boot up and why my raid arrays are not found and booted up correctly.

If it succeeds, I'll post a bit more here.
Rick

Grub is not installed correctly because you used the live cd, not the alternate install cd which you should use for raid.
You could still just add grub, read here about installing with the live cd and skip the step of the actual install (because you already installed it), just focus on the starting steps to confirm the live cd can see your array, and then the steps to install grub.
[https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29](https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29)

Also, if your windows is on the separate disk, it's much better to use software raid than the motherboard based fakeraid. Fakeraid is used when both windows and linux need to be on the array because thee is no other way currently.
For only linux on the array software raid is much better. On top of that I would use LVM too, it's much better because you don't have to spend too much time calculating what size to create your partitions. You can resize them easily later even while ubuntu is running.

---

### Post by rickbeton on 2010-02-25
> Grub is not installed correctly because you used the live cd, not the alternate install cd which you should use for raid.

Ahah! That's useful to know.

I'm not using fakeraid, although the P55 mobo has two different raid controllers on-board.

---

### Post by rickbeton on 2010-02-26
I installed 9.10 using the alternative CD and the RAID works fine.  Thanks for the advice.

---

### Post by rickbeton on 2010-02-26
@kat3c please could you mark this thread SOLVED using the 'Thread Tools' menu near the top.  That'll help other people looking for similar solutions.

---

### Post by kat3c on 2010-02-26
> **rickbeton said:**
> @kat3c please could you mark this thread SOLVED using the 'Thread Tools' menu near the top. That'll help other people looking for similar solutions.
 
 
 
You got it!

---

