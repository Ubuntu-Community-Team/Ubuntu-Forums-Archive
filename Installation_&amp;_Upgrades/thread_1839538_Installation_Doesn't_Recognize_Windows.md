---
title: "Installation Doesn't Recognize Windows"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by DonBiColorado on 2011-09-05
My computer is an Asus M4A77D with an AMD Athlon II processor, Running Windows 7. 
I am trying to install Ubuntu 10.04.1 from the DVD.

The computer has two hard drives: a SATA drive hosting Windows, and an EIDE drive that is empty.  I want to install Ubuntu on this drive.

The installation routine shows only the empty drive, and displays a messsage that there is no operating system installed on the computer. I can't see the Windows disk.  I went through this problem a while back, and while Unbuntu installed OK, I was unable to boot Windows. 

What am I missing here?

---

### Post by YannBuntu on 2011-09-06
Please could you boot on your UBuntu DVD, then follow this tutorial and indicate us your resulting BootInfo URL ?
[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

it will help us understand how your drives are recognized.

---

### Post by dino99 on 2011-09-06
> **YannBuntu said:**
> Please could you boot on your UBuntu DVD, then follow this tutorial and indicate us your resulting BootInfo URL ?
[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

it will help us understand how your drives are recognized.

note: ubuntu should get the latest gparted 0.9.0-7 as it fix a ntfs resizing issue. Have reported bug #827213
Better to use the latest partedmagic

---

### Post by Mark Phelps on 2011-09-06
> **DonBiColorado said:**
> 
The computer has two hard drives: a SATA drive hosting Windows, and an EIDE drive that is empty.  I want to install Ubuntu on this drive.

OK, so do the following:
1) Disconnect the Windows drive from the PC
2) Install Ubuntu to the EIDE drive, using the whole drive
3) Reconnect the Windows drive -- but continue to boot from the Ubuntu drive (may have to change your BIOS settings to do this)
4) Once into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB menu and add an entry for Windows.

When you reboot, you will see a GRUB menu.

---

