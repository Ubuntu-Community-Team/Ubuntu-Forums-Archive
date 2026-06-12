---
title: "kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by dangle42 on 2014-08-04
Hi, 
Here is my problem. My computer (Asus motherboard A8N SLI-Deluxe, AMD-64 processor, 3G Ram, 500GB SATA) had trouble installing Ubuntu 14.04. It would usually crash on install. If it did successfully install, then it would crash during a session with a kernel panic message after repeated system error messages. Of course I tried a reinstall using several different versions and images with little luck. I then decided to upgrade the BIOS thinking that it might help compatibility and driver recognition. I installed Windows XP and successfully updated the BIOS. Then I put the Ubuntu Live DVD in again and got the message: kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0). I tried several things including new DVDs, different versions and a copy of Mint. I tried to access the menu using the shift key and I tried the Noapic option as was recommended by a few posts with no luck. If I do get to the next load screen (the purple screen with dots), it inevitably freezes on one of the dots. I also tried a trick to put the .iso onto the hard drive itself and run the .iso from the grub menu. I get the same result. 

Here's what I don't have a problem with:
Corrupted disks (the hash check out and they worked on other computers)
A bad hard drive (it's new and works on other computers)
The DVD drive (I used another one with the same results)

The BIOS doesn't have a USB boot option so I can't try that. Is it something in the BIOS itself that I can change? I ask this question because I didn't get this error until the BIOS update.

---

### Post by wb5hqh on 2014-08-09
On my gigabyte brix, i had to add the newest kernel to get it to load. I put the drive on my laptop and booted it up and then add the kernel. Put the drive back into my Brix pro and away it go.

---

