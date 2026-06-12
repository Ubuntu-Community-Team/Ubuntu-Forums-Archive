---
title: "Boot loader question"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by demorik on 2009-12-02
Ok here is the deal, i have a pc with two hard drives a 60gb and 300gb, whenever i want to dual boot ubuntu with windows on the same drive i have always installed ubuntu second so that grub is the boot loader, so what i wanted to do was instal windows xp on the 60gb first (xp will be used for work so i cant experiment with dual booting on this drive) then on the 300gb i was then planning to partion and then instal windows 7 second and the ubuntu 9.10 last, my question is would the ubuntu boot loader see and boot the xp drive or would i have to set it up to do so?

---

### Post by darkod on 2009-12-02
It will, but install them exactly as you said. Windows combines the bootloaders for two versions. When you install win7 it will combine XP boot inside. Then ubuntu will detect the combined one and add it. It should show just one entry for windows in grub menu but then after that it will ask you 7 or XP.

Also, it's a good idea after installing XP to change the boot order of the drives in BIOS and set the 300GB as first choice,before installing 7. And do not disconnect the 60GB, let the system know it's there. Some people would say disconnect your first drive and install 7. I can't agree with that, it needs to know the drive is there and it has XP on it.

When installing ubuntu make sure grub2 will be installed on the 300GB (depending if it will be named sdb or sda). You can check that in the last step, before clicking Install click on Advanced and it will show you where it plans to install grub2. If it's the 300GB disk no need to change.

---

### Post by presence1960 on 2009-12-02
**+1 **I too see no need to remove a disk to install windows. All that needs be done is set the disk you are installing windows onto as first in the hard disk boot order in BIOS. This is necessary because windows will write it's bootloader to the first disk that boots. So even if you install windows 7 on sdb, if sda is the first disk to boot then windows will attempt to write the bootloader on sda.

It is this process of windows writing it's bootloader to the first disk in BIOS to boot that has led to the totally untrue myth that windows needs to be on the first partition of the first disk. Windows only requires a primary partition- it does not matter if it is the first, second, third or fourth partition on the disk as long as it is primary. I have had windows installed on the fourth partition(primary of course) and had no problem booting it from GRUB.

---

### Post by oldfred on 2009-12-02
The windows boot loaders combine boot into the windows with the boot flag on. It is the way to choose which windows to boot.

If you want to directly boot either windows from grub you can, but then will not be able to choose in windows which to boot. You should not have to disconnect a drive as long as the second install does not see a boot flag.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by demorik on 2009-12-02
Yea i definately wanted to use grub as the boot loader, thanks for the info guys.

---

