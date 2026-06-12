---
title: "Please help me get this fixed"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by Colo2 on 2010-03-18
Every time I try ubuntu on my laptop, I have the same problem.

So, My laptop had Vista on it, I wanted to dual boot with Ubuntu. It didn't work.

Now, since a full format and installation of Windows 7, I wanted to try ubuntu as a dual boot again. 

Same problem

The problem is as follows;

I boot the LiveCD, and instantly I get a scary error telling me that one or more disks are failing. Its telling me that my hard disk is going to die :(

I ignore the message and try and install. It won't let me resize the windows partition. So i try with gparted. In gparted, the partition I want to resize has a yellow triangle warning sign next to it, and it won't let me resize it. 

I've tried booting into windows, defragging twice, chkdsk /f
Always the same problem

I dont think my hard drive is failing because I have absolutely no problems installing windows, and the laptop works as fine as it did a year ago when I bought it.

I would love for someone to help me fix this problem once and for all, I would love ubuntu on my laptop.

Thanks ;)

Tom

---

### Post by howefield on 2010-03-18
Try resizing your Windows partition with Windows Disk Management software (that comes with Windows 7), then install Ubuntu to the empty space ?

---

### Post by Colo2 on 2010-03-18
Hey
I will try that and get back to you, thanks for the suggestion :D

---

### Post by underquark on 2010-03-18
1] Partition the disk using about half the available space and install Windows into that partition.  Then install ubuntu "along side" Windows, i.e. using the remaining available space and dual-booting with Windows.

OR
2] You've already installed Windows.  Turn off any page files/swap files and turn off any restore points - this removes any fixed parts of the disk and allows a successful defrag to take place.  Defrag the hard disk with Windows.  Resize the partition from within Windows (GParted often does't want to risk damaging things by trying to defrag a Windows partition).  Then install ubuntu with the dual-boot option.

---

### Post by Colo2 on 2010-03-18
What are the advantages and disadvantages of instlling Ubuntu within Windows?

---

### Post by howefield on 2010-03-18
> **Colo2 said:**
> What are the advantages and disadvantages of instlling Ubuntu within Windows?

Do you mean installing with the Wubi installer ?

Advantages
Ease (no messing with partitions)
Remove via control panel/add-remove programs.

Disadvantages
Performance hit (may not be so noticable)
Windows goes up in flames, so does Ubuntu.
File system may be less reliable.
Used to be hibernation issues - don't know if still an issue.
Possible run out of space - through not allocating enough space initially.

Suitable for short term use, because of the disadvantages. If you like what you see then a real dual boot is much preferable.

---

