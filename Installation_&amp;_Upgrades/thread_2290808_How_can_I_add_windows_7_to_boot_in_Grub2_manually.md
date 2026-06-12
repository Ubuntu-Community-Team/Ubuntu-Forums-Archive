---
title: "How can I add windows 7 to boot in Grub2 manually?"
date: 2015-08-15
forum: Installation &amp; Upgrades
---

### Post by zorrohere on 2015-08-15
I had windows 7 at sda1 and windows 8 sda9 but after installing Linux, grub detects windows 8 at sda1. So how can I add windows 7 to grub manually?

---

### Post by Bucky Ball on 2015-08-15
Welcome. Have you tried opening a terminal and:

```
sudo update-grub
```

?

---

### Post by zorrohere on 2015-08-15
Yes I tried that, it detects windows 8 only. What is confusing me is, windows 8 is at sda9 but it is detected at sda1 where windows 7 is installed. So I didn't go ahead with manually adding windows 7 to grub.cfg.

---

### Post by grahammechanical on 2015-08-15
The update grub command will detect Windows boot loaders. So, it is likely that Grub is seeing the Windows 8 boot loader in a Windows boot partition (sda1). It would be useful for you to attach a screen shot of your partitions. There should be a windows program that will let you see your partition layout and a screen shot utility. It will also be useful if you added the full printout of the sudo update-grub command so we can see what you are seeing.

Regards.

---

### Post by yancek on 2015-08-15
Windows 7 'usually installed as MBR while windows 8 'usually' installed UEFI.  Do you remember which you did for each system?  If you can boot Ubuntu, you should be able to get partition information to post here.  If 'sudo fdisk -l' doesn't work, use GParted partition manager.  It should be on the Ubuntu install media or you can install it to your hard drive.  When you see the boot menu for windows 8, do you see another option for 7?  Posting partition information will be helpful so we can see which partitions are actually windows.  Windows 7 almost always created a small boot partition and that was usually shown as sda1.

---

### Post by Mark Phelps on 2015-08-15
If you have a BIOS-MBR machine, Win8 will not force UEFI on you -- I know because I've install in just this situation.

What does happen, if you have Win7 already installed, and install Win8, if it sees Win7 (e.g., in another partition on the drive), it will update the boot folder for Win7 with the Win8 boot loader info.  When that happens, os_prober can then see two Windows installs -- one for each version.  This is not a serious problem, as only one of the lines in the GRUB config file will actually work.  It's typically the second of the two.

---

### Post by Bucky Ball on 2015-08-16
> **zorrohere said:**
> So I didn't go ahead with manually adding windows 7 to grub.cfg.

Don't. Never edit that file. Edit /etc/default/grub then 'sudo update-grub' will write the changes to grub.cfg.

---

### Post by oldfred on 2015-08-16
Only if you had installed the second copy of Windows to a primary partition could you possibly repair it so it could have boot files of its own. Then grub could directly boot it.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

---

