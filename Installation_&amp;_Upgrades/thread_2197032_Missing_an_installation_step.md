---
title: "Missing an installation step"
date: 2014-01-01
forum: Installation &amp; Upgrades
---

### Post by gabe.labounty on 2014-01-01
Hi everyone! I can't go 2 minutes into the installation without a problem. I burned my blank DVD, chose Windows 64 bit, then the wubi installed on the CD. It gave my two options, to try ubuntu or go to the community. I chose try Ubuntu, then tried all three options (reboot now, reboot later, or fix CD). When I hit reboot now, it didn't do anything. When I fixed the CD, it said it failed because of a file in my temp folder. I took out the CD, and when I tried to put it back, my laptop spit it back out. I figure this is something so stupid, but to be on the safe side I would rather have a real person help me finish out the installation.

---

### Post by Bucky Ball on 2014-01-01
I can't help with the wubi stuff (not many can as not many here use it) and just a tip. Wubi is no longer supported and probably not the way to go. You would be better to install Ubuntu as a dual-boot if you are wanting to keep Windows. Good luck. ;)

---

### Post by fantab on 2014-01-01
> **Bucky Ball said:**
> Wubi is no longer supported and probably not the way to go. You would be better to install Ubuntu as a dual-boot if you are wanting to keep Windows. 

+1.

If you need further assistance with installing Ubuntu along with Windows, you must give more info about your existing machine, like:
What Windows Version? Laptop or Desktop?
Did Windows come pre-installed with your machine?
Does your machine use BIOS or UEFI?
What are the hardware specs of your computer, RAM, CPU, Graphics Card, etc.?

---

### Post by gabe.labounty on 2014-01-01
I just followed the steps on the download page- so how should I dual boot and avoid wubi?

---

### Post by fantab on 2014-01-01
> **fantab said:**
> 
What Windows Version? Laptop or Desktop?
Did Windows come pre-installed with your machine?
Does your machine use BIOS or UEFI?
What are the hardware specs of your computer, RAM, CPU, Graphics Card, etc.?

What Ubuntu version are you trying to install?

---

### Post by gabe.labounty on 2014-01-01
[h=3]13.10. I'm on a laptop, BIOS, and 3 GB RAM. What is the best way for me to install?[/h]

---

### Post by fantab on 2014-01-02
Before we go into the details, boot with the Ubuntu 13.10 DVD/USB and choose "Try Ubuntu without installing". Then open Terminal [Ctrl+Alt+T], run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```

This should tell us how your HDD stands with respect to partitions and available space... Will guide you further based on the info you post.

---

### Post by Bucky Ball on 2014-01-02
Make free space on your hard drive to install Ubuntu to. Ubuntu will exist happily in an extended partition so stick to the four partitions on one physical drive. Are you running Win 7 or 8? If you get into the BIOS, see how they are booting. Is Win booting using UEFI?

Don't bother about creating partitions with Windows to install Ubuntu to, just leave free space, when you get to the partitioning part of the Ubuntu install, choose 'Something Else'. Manually partition. If this means putting Ubuntu and its partitions on logical drives inside that, all good. You can have three primary partitions (Win must be on a primary partition) and an extended (inside which you can make as many logical partitions as you like ... theoretically, as many as your hardware can handle, actually.

---

