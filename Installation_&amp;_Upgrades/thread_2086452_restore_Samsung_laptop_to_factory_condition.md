---
title: "restore Samsung laptop to factory condition"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by parminides on 2012-11-21
This isn't an Ubuntu issue per se, but I hope someone on the forum can help me.

I bought a Samsung Series 5 Ultra 14" Notebook (Model number NP520U4C-A01UB) a few days ago with Windows 8. There were problems with the wireless right off the bat (Intel Centrino Advanced-N 6235 (rev 24)). Wireless randomly disconnected or didn't connect at all. Sometimes troubleshooting in Windows fixed it, sometimes not.

I moved on to installing Ubuntu as dual boot with Windows before resolving that issue. That was a big mistake.

I installed Ubuntu 12.04 with a live CD. I encountered similar wireless networking problems in Ubuntu. I discovered that other people have had similar problems in Windows and Ubuntu. None of the solutions for either OS worked for me.

I got fed up and decided to restore the computer to factory specs and return it. I booted up to the Windows recovery partition. It was taking a long time, I wasn't at home, and I had to be somewhere, so I aborted the recovery. I didn't worry at the time because it had a message like, "if recovery doesn't finish, start over from the beginning."

Despite the message, aborting the recovery turned out to be another big mistake. The computer hung up when I tried to recover Windows later.

I worked around this problem by running gparted from the live CD. I don't remember exactly what I did, but think I deleted the Windows and Ubuntu partitions and replaced them with a single one formated ntfs (for Windows). Whatever I did, I was able to restore Windows with the recovery partition.

I tinkered around with the wireless some more and got optimistic enough to try reinstall Ubuntu. (I had read in a forum post that 12.10 could deal with the newer wireless hardware.)

Unfortunately, the installer didn't recognize any existing operating systems (see somethingelse.jpg). I didn't know enough to install Ubuntu with the "something else" option, but I've attached screen shots to show how the partitions looked at that step (see install1.jpg and install2.jpg).

I've also attached an image of how gparted shows the partitions (gparted.jpg).

I've again reached the point where I just want to return the laptop to the store. I've tried all the tricks to fix the wireless in Windows, and I'm convinced that I have a hardware problem. The laptop had these wireless problems right out of the box.

However, the recover feature for Windows apparently only restores the Windows partition to factory specs. I think I need to restore all partitions to their original states. I might not be granted a refund if there's any hint that I've added another operating system or otherwise tinkered around with the partitions.

I'm in over my head on this one. Does anyone know how I might restore the entire hard drive (not just the Windows partition) to its original condition? I did not make an image of the disk.

It may just be matter of giving /dev/sda4 the proper label (Windows?) and fixing /dev/sda3, which currently has an unknown file system. But what's up with that free space? (I realize that I have to delete /dev/sda7 and expand /dev/sda4 to fill the space.)

Any guidance would be greatly appreciated.

---

### Post by parminides on 2012-11-21
I removed Ubuntu from the BIOS boot menu. I deleted the ext4 partition and recaptured that space for Windows 8.

I guess the only thing that still bothers me is that if I start an Ubuntu installation from a liveCD (only as a test), it says, "This computer has no detected operating systems." Since it recognized the Windows partition previously, things must not be restored as they were before.

Is this related to the free space "gaps" between some of the partitions? Is there any way to get this laptop back to its pristine state so that I can return it worry and guilt-free?

Do you have any recommended replacement laptop/notebook models that run Ubuntu relatively carefree? What I liked about the Samsung was that it was small but had a large hard drive (750GB) and a CD/DVD drive. These were big plusses since I'm not yet a big fan of the Cloud. I also really liked the dull finish of the screen, which cut down on glare.

---

### Post by oldfred on 2012-11-21
Because you have Windows 8 on a new computer you have secure boot with UEFI. Did you turn that off to get 12.04 to install? You have to use 64 bit version and boot that in UEFI not in BIOS/legacy/AHCI mode.

I thought only 12.10 installed with secure boot. But 12.04 will be upgraded to grub2 2.00 with the next point release to allow secure boot.

If you did not document or backup system before installing, not sure if just running recover restores it totally or not.

---

### Post by parminides on 2012-11-21
I did turn off secure boot to get 12.04 to install. In the absence of suggestions, I'm going to return the laptop and cross my fingers.

My wish list for its successor:

1. 13-14" screen
2. 750 GB hard drive
3. 8 GB memory
4. dull screen (to minimize glare)
5. CD/DVD drive

Does anyone know of such a creature that works well with Ubuntu 12.04 or 12.10?

---

