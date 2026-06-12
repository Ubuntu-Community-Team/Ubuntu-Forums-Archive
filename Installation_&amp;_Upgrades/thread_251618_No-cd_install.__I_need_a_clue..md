---
title: "No-cd install.  I need a clue."
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by bbalpha on 2006-09-05
I've looked around for information on a no-cd installation of Ubuntu and I feel like I'm making some progress, but I've hit a stumbling block.

The machine: XP, 2 physical drives (one is NTFS, the other is FAT32 and sufficient unpartitioned space).

The goal: Install Ubuntu to the second drive and set up a dual boot.  Currently, instlux is working via GRUB for NT.  I can get to the installer.

I have a copy of the alternate install iso saved to the FAT32 partition of the second drive.  I also have a copy of the LiveCD iso, which I've used a bit with QEMU, but it won't read outside of the filesystem image it creates so as to be useable for installation.

I was hoping to use the shell during installation, mount the iso as a loopback device and install components from there.  Alternatively, I could go for a net install but my sole means of internet access is through a USB wifi device which doesn't get recognized by the net installer.

Either answer would work for me; Is there a way to load up drivers for the USB network interface (a D-link WUA-1340) prior/during the net install?  Or mount the iso from within the BusyBox Ash shell for a 'cd' installation?  I've tried varying mount commands, but it seems like my lack of Linux knowledge is keeping me from getting it right - or not knowing for certain that this is not possible with the tools available.  My best hunch is that I can't access the iso image to mount it.  For the other, it seems like I'd have to build my own initrd if I want to have the USB D-link device drivers loaded.

I've requested a cd be shipped to me, but I was hoping to do this sooner than having to wait the two to ten weeks for the cd to arrive.

Does anyone happen to know the solution to this off the top of their head?

Thanks for the help in advance.  =)

---

