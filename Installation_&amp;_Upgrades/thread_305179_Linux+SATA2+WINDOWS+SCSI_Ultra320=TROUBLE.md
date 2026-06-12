---
title: "Linux+SATA2+WINDOWS+SCSI Ultra320=TROUBLE?"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by keka on 2006-11-22
Hi, I am fairly new to Linux and Ubuntu. As of right now my set up is like this:

Dual disk boot of Windows on SATA2 drive and Ubuntu on IDE drive.

What I want to do and I already purchased the necessary parts for it is to have:

Dual disk boot of: Windows on SCSI Ultra320 68pin disk and Ubuntu on SATA2 disk. 
Another options is to keep Ubuntu on it's current IDE drive as a slave, and just install a fresh copy on WIN on new SCSI Ultra320 68pin. How do I go about this?

I've heard that some people recommend having Linux on IDE for some reason, since bios reads it as the main disk by default, don't know if that's true. I am not sure if this is possible to do, but have a feeling it is. If anyone who's every done anything similar to this set up, please share your experience and help me get through it more easily. Any ideas and suggestions would be greatly appreciated. Thanks very much!

---

### Post by jpkotta on 2006-11-22
Linux works with SATA 2 drives and you can configure grub (the bootloader) to work with many configurations of drives and OSes.  It should configure itself the right way automatically, but if it doesn't, the forums will help you.

For reference:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

