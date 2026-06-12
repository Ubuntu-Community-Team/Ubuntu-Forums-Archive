---
title: "Cannot boot from USB pen drive"
date: 2017-01-31
forum: Installation &amp; Upgrades
---

### Post by dusty1980 on 2017-01-31
No help.  I have every USB option listed above the installed internal hard drive and the laptop will not boot to the usb flash drive.  

One thing I have noticed when using Rufus to produce the bootable drive of the Ubuntu mate iso file, when I select NTSF as the format, then select the iso file, Rufus changes the file format back to F32.  

I have tried booting another laptop with the USB drive and Ubuntu Mate does load.

---

### Post by sudodus on 2017-02-01
@dusty1980,

You might have a completely different problem than that of the original poster of this thread. I think it will be easier to solve your problem, by separating your posts into a separate thread, which will be your own thread. I will ask a moderator to do it, and I think I will find this particular post in your thread, and I will be able to continue helping you there.

---

### Post by Perfect Storm on 2017-02-01
Post splitted to new thread.

---

### Post by dusty1980 on 2017-02-01
I can try elementary.  Why would it be more likely to boot to USB?  Seems like my laptop doesn't even try booting to the USB flash drive.

---

### Post by howefield on 2017-02-01
> **dusty1980 said:**
> I can try elementary.  Why would it be more likely to boot to USB?  Seems like my laptop doesn't even try booting to the USB flash drive.

Just to say, "try elementary..." is part of Artificial Intelligences signature, it appears on all posts and is not offered as a solution to your issue.

---

### Post by sudodus on 2017-02-01
This particular computer does boot Ubuntu MATE from the pendrive, but other computers boot from it. We need information about the computer.

Which version of Ubuntu MATE is it,

- (16.04.1 LTS or some other version)?
- 32-bit alias i386 or 64-bit alias amd64?

Please specify the computer hardware, (at least)

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and tell us if you boot in UEFI mode or BIOS mode (if Windows 8-10, you probably boot in UEFI mode, if Windows 7 maybe).

Finally - what happens when you try to boot from the USB pendrive, please describe the details.

---

### Post by dusty1980 on 2017-02-03
Ubuntu-Mate 16_04 LTS i386

Gateway
M-150X
Windows Vista Home Premium - Service Pak 2
Intel Pentium Dual CPU T2310 @ 1.46 GHz
ACPI x86-based PC
2.0 GB Memory
32-Bit Operating System
File System - NTSF
Mobile Intel 965 Express Chipset Family
Realtek RTL8187B Wireless 802.11g 54Nbos USB 2.0 Network Adapter

---

### Post by sudodus on 2017-02-04
I think the original 16.04 version has an issue with your graphics chip, but the first point release, 16.04**.1** LTS is debugged, and works better.

I think your computer should work with Ubuntu MATE. Another alternative is Xubuntu. The third alternative, Lubuntu has an even lighter desktop environment.

-o-

But first the computer should boot into the install drive. Is there a working CD or DVD drive? If 'only' a CD drive, you can try to boot Plop and chainload to the USB drive according to this link and links from it,

[Installation/FromUSBStick#PLoP_Boot_Manager](https://help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager)

There is even a version of Plop for a floppy disk.

---

### Post by dusty1980 on 2017-02-05
So I finally was able to boot to the USB stick.  I changed USB ports and now it works.  I have successfully installed Mate.  Now I'm off to trying to figure out how to install Juno dialup for my Mom.  I donwload the software from Juno site, but it doesn't open like in Windows.

---

### Post by yancek on 2017-02-05
> Now I'm off to trying to figure out how to install Juno dialup for my Mom

Good luck with that.  I haven't seen anything that would work with most Linux including Ubuntu.  If the software file you downloaded has an '.exe' extension, don't bother.  It won't work on Linux.

---

