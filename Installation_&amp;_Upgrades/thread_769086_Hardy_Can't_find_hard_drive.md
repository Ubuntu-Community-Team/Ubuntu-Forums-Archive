---
title: "Hardy Can't find hard drive"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by rmccarri on 2008-04-26
Hi,
I have been running Ubuntu 7.10 i386 on a computer with an AMD Athlon 64 processor and a Western Digital 250 GB SATA hard drive.

I tried the online upgrade to 8.04 LTS and everything went fine until I rebooted.  I got the splash screen, but it sat there for a very long time and then spit me out to an ash terminal window.  I downloaded the install CD and when I get to the partitioning screen, there is no drive detected.  Just to make sure, I reinstalled version 7.10 from a CD fresh with no issues whatsoever and then tried to upgrade to 8.04 over the internet and had the same problem.

Since then, I have downloaded and tried installing both the i386 and the AMD64 bit versions of Ubuntu and Kubuntu as well as Fedora Core 8 and Open SUSE 10.3 and all have the same problem.  The install CD cannot find the hard drive.  I've tried changing every BIOS setting for my hard drive to no avail.  Has anyone else noticed this type of behavior where older Linux versions install fine, but the newest batches have problems finding your SATA drive?

Any help would be greatly appreciated.
Thanks,
Rob

P.S.  One more note, I have pretty much the same computer at work running 7.10 Server Edition and it took the upgrade without any issues whatsoever.  It's pretty weird.

---

### Post by janosaudron on 2008-04-26
Exact same problem here, on Ububt 7.04 i can see all of my Sata Hdd but when i try to install from any variant of 8.04 i don't see any of my hdds, i'm trying to install on a WD 250gb hdd and it's running on an ECS P965T-1 Mmobo, i've played with all ide settings i can find on the bios, tried to plug only the main hdd on every sata slot, i'm running out of ideas

---

### Post by rmccarri on 2008-04-27
Woo Hoo!

I seem to have found a fix.  The problem is with the VIA chipset on my motherboard.  The fix is to go to more option on the LiveCD and add 'pci=nomsi' without the quotes to the boot options.  I hope that this helps other people!

---

