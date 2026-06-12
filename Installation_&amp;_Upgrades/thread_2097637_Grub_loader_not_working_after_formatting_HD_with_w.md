---
title: "Grub loader not working after formatting HD with windows recovery"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by 4esa on 2012-12-23
Hello, as a Christmas present for my mum I decided to give her my old laptop. Without thinking about having Grub and other Linux stuff on it I went into the Windows Recovery menu on my ACER ASPIRE ONE D150 NETBOOK WITH WINDOWS XP and allowed it to format my computer back to factory settings. It was not done from a disk, but by a partition as it doesn't have a CD drive. I restarted the computer with the Hard drive as first boot priority and I received this message: 

[I]error: no such partition
grub rescue[/I]

Thinking that I would just reinstall Ubuntu so I could get into my computer I decided to boot off my live ubuntu USB. Unfortunately, even top priority I could boot from the USB without the same error message. I have browsed the internet for hour looking for help, but most of it I couldn't understand or was a dead thread. Please help me. Direct instructions of what to do would be the best, as I basically know nothing about linux, Ubuntu and Grub. A suggestion was to turn off quickboot to stop Grub from loading, but that has no effect.

Note: I do not have a CD drive, but usually it can boot off a USB. I can't access the windows boot recovery any more because I do not have a menu to load a partition.

I just want to be able to access the formatted windows partition. I don't want GRUB or Ubuntu.

I really need help before tonight, as that's when we give our presents.
**Thanks in advance  **;)

Edit: If ls means anything to you guys this is what it returns: (hd0) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)

---

### Post by Bucky Ball on 2012-12-23
Try Boot Repair. You can make a bootable CD or install into a LiveCD boot and Try Ubuntu. (Yes, it will install in a liveCD boot from Software Centre.) Find instructions here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 4esa on 2012-12-24
Thanks a lot for the link. The USB not loading was still a problem, however I found an external USB CD drive in my house and used it to load the boot repairer. When I restarted I was taken directly to the windows xp partition. I have no idea where GRUB or Ubuntu are but everything seems fine. Thanks!

---

### Post by Bucky Ball on 2012-12-24
Great news. In Linux language, the grub will be installed on sda1, where the Win bootloader is. That is the first partition, first drive, and default unless you manually choose to put it elsewhere.

Enjoy!

---

