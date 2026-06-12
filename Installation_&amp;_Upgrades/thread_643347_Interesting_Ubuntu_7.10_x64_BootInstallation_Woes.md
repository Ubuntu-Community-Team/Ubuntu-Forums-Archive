---
title: "Interesting Ubuntu 7.10 x64 Boot/Installation Woes"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by Lightloch on 2007-12-17
I have been working and researching this problem for quite a while now, and I have not been able to turn up any solution thus far. I have read many seemingly-similar posts, but none directly related to my problem, and those users - unlike me - are at least able to see a colored screen, logo, get to a terminal, etc. My PC's specs are below to be available for troubleshooting and suggestions:

ASUS Crosshair Mobo
AMD Athlon 64 X2 6400+ BE (AM2)
4GB Crucial Ballistix DDR2 800 RAM
BFG GeForce 8800 GTX OC2E 768MB GPU
150GB WD SATA Raptor (Main Vista drive)
1TB SG SATA (Storage for both OSes)
160GB WD SATA (Main Ubuntu drive)

All components have sufficient cooling and temperatures are nominal in all parts.

I use full Windows Vista x64 Ultimate as my main OS (150GB drive). As mentioned above I have the separate SATA 160GB drive installed that is my Ubuntu-only drive that Windows  neither sees nor touches. 

So when I first got everything setup and Windows installed and running great a while ago, in went my Ubuntu 7.10 x64 DVD. The disc booted and eventually installed just fine and all was well. I installed the suggested video drivers and got everything functioning well, GRUB doing its job correctly, etc. I am able to boot into both Vista and Ubuntu just as I wanted/dreamed various times without problems.

BAM! A few days later, I attempt to boot into Ubuntu, a black screen with a couple lines of text is shown (Linux kernel alive, etc.), and then the PC simply goes to a black screen with nothing on it, and continues to do the same thing for many days when trying to get into Ubuntu. Windows keeps going just fine. Safe graphics mode does the same thing. 

So then I decide to completely format my Ubuntu drive and start from scratch. I wipe the drive, restore my Vista master boot record from my install disc, Windows works/boots fine, and I then insert my Ubuntu DVD to install once again... same problem! First a black screen with a few lines of text as if everything is going fine, then seconds later to a solid black screen that stays forever until I hard-restart my PC. Nothing ever happens if I let it sit forever.

Yes I have tried booting into both normal and safe graphics mode and it just does the same thing. What boggles me about this whole thing is that Ubuntu booted and worked great for a few days and then this happens all of the sudden, and continues to happen even after a complete format and re-attempt, and now not even the disc alone will boot.

As I said I have read many boards, done many searches, and cannot turn up any solution. Any help will be greatly appreciated! Thank you! :)

---

### Post by Pumalite on 2007-12-17
Did you allocate space for Ubuntu with Vista partitioner first? This is vital. You cannot just partition with the Live CD. Otherwise, Vista doesn't let you run anything in that computer.

---

### Post by Lightloch on 2007-12-17
Do I need to do that even if I use the completely separate drive for Ubuntu? When my first installation actually worked, it allowed me to select my third, unused drive for the Ubuntu installation (it was shown as unallocated space and was then formatted within the installation for Ubuntu's file system).

As I mentioned everything worked perfectly for at least a few days and then my endless black boot screen problem started and even continued in my second installation attempt. I assumed that this error was somehow graphics related, but there is no apparent way to change anything if that is the case.

---

### Post by Pumalite on 2007-12-17
Sorry; I wasn't aware you installed in a separate drive. The requirement is not valid then.

---

### Post by Lightloch on 2008-01-19
This problem is so irritating. From what I can by searching here and the net hundreds of people if not more have this same problem. Has anyone found the solution yet? This is a terrible bug in 7.10 apparently. I am sorry I dished out the cash for the fancy printed discs from Canonical.

---

### Post by Pumalite on 2008-01-19
Boot your Live CD and, from the Terminal, post:
sudo fdisk -lu
(we'll mount your partition once we get that and check menu.lst)

---

