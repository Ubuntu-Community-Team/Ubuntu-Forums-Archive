---
title: "Need help with Install please!"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by NeXplicit on 2008-02-17
Hey everyone,
     I am having some trouble trying to install Xubuntu Fiesty Fawn (7.04). I downloaded the desktop cd image, burned the image to a cd, and booted it up. Works fine but my problem is the partitioning part. 

I have Windows XP on my current hard drive and I would like to delete my current partitions and wipe my hard drive. Would like the file system to be FAT32 so that I can file share with Windows PC's. I have tried doing the Guided - Use Entire Hard Drive, does fine until it is installing then gives me an error saying it was a failure. Then I try and do manual, do everything I need to make the main partition and the swap, when i try to continue it tells me that i need to specify the root file system for the partition table.

I have never used any kind of Linux programs before so I am new to it. The PC i am putting it on to is a mini computer with a Pico Motherboard about 500MB of RAM and an 8GB Flashcard Hard Drive.

Need help quick this is for my Computer Networking class, im doing it as a project.
       
   Thank You.

---

### Post by Pumalite on 2008-02-17
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete everything in your hard drive. Make new large partition of your whole hard drive formatted whatever you want. Install Ubuntu, Guided>Use Entire Disk

---

### Post by NeXplicit on 2008-02-17
I don't know how to use Gparted, I made a LiveCD and booted it up and I get CLI, what do I do after this to set it up so I can delete everything on my hard drive?

---

### Post by wpshooter on 2008-02-17
> **NeXplicit said:**
> I don't know how to use Gparted, I made a LiveCD and booted it up and I get CLI, what do I do after this to set it up so I can delete everything on my hard drive?

Nex:

    Using another computer, go to [www.killdisk.com](www.killdisk.com) and download Killdisk program and put it on a CD and boot to it in the computer that you are trying to put Ubuntu on and use Killdisk to WIPE the hard drive completely clean.

    Then go back to your Ubuntu CD and boot to it and try the installation again.

     However, with the amount of memory that you have, I believe that I would give Ubuntu/Gutsy a shot instead of trying to install Xubuntu/Feisty.

     P.S. - You might have a better chance of success, if you tried using the ALTERNATE CD version to do the installation instead of the DESKTOP/live CD version.

    Good luck.

---

