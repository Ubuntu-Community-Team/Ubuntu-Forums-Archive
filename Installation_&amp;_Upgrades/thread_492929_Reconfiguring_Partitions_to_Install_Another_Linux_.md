---
title: "Reconfiguring Partitions to Install Another Linux Distro"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by hermesrules on 2007-07-05
Hi,

I have been trying to figure out a way to install Ubuntu Feisty alongside OpenSuse and XP. At the moment I am using OpenSuse exclusively, the XP is there for just a few applications (most notably MS Access), and am now trying to figure out a way to add Ubuntu to that list.

I have a "mature" laptop (nearing its 4th birthday) , have four partitions on my local HD, and four partitions on an external disk that I connect through USB. The setup of the local HD is the following:

hda1 - Windows XP (18 GB)
hda2 - ext3, \ (10 GB)
hda3 - swap (1 GB)
hda4 - I mean this to become the \boot partition, it's about 100 MB

The setup of the external HDD is:
sda1 - fat32 (30 GB) - meant for sharing files
sda2 - ntfs (120 GB)
sda3 - \home
sda4 - \ - this is to become root for the second distribution, but I don't want it mounted in OpenSuse.

Last night I tried to install XUbuntu (with the intention to download and install gnome-desktop later), but possibly due to a burning error, it hung at the end of the install before installing Grub, so even though all files are where they are supposed to be, I can't boot into the newly installed distribution.

Having thought about it a bit more, I think I should use the same \boot partition for both Suse/Ubuntu/whichever other distro I would like to use.

So my questions are:
1. How can I move my current Suse's boot directory's contents onto the separate \boot partition? How should I then change the grub settings, to let Suse know the kernel is someplace else?

2. Will 100 MB be enough to hold a typical OpenSuse kernel, and a typical Ubuntu kernel? Alternatively, what size would you recommend?

3. How do I preserve my OpenSuse grub - it is much nicer than that of Ubuntu. Will it be possible to run OpenSuse installation in recovery mode, and then reinstall Grub from there once I have completed all other operations?

I have already decided to use the same \home partition for all systems, with different user names, so no data should get damaged.

Your help is greatly appreciated! Thanks!

---

### Post by hermesrules on 2007-07-07
Well, it turns out that I had to give up my plans for adding another distribution to my machine. For a reason, which I do not completely understand, it turns out that the root partition cannot reside on an external HDD, which is connected via usb to the laptop, but also through a PCMCIA card (the laptop is old enough, and does not have internal usb 2.0).

What happens is it boots, but can't seem to continue. Even thought the boot partition is on the local drive, it does not seem able to load the kernel or the drivers needed to continue the boot process.

I'd be curious to hear, however, if anyone has had a different experience trying to run a linux distribution off an external HDD.

---

