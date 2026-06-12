---
title: "Ubuntu installer not detecting partitions"
date: 2013-11-28
forum: Installation &amp; Upgrades
---

### Post by kiranvinayan on 2013-11-28
Laptop: ASUS X550C-X0029D
The laptop came with just DOS. I installed Windows 7 Ultimate(64 bit) and deleted all the partitions and created a 100GB parition for Windows. Then I used EASEUS parition manager and created a 300GB NTFS parition. There is a 100MB GPT parition also.
When I tried to install Ubuntu 12.04.3, the installer does not detect Windows 7. When I tried to create the partition for Ubuntu manually, it shows the hard disk without any of the exisiting paritions. 

I ran sudo gparted and got the attached screenshot.

How can I install Ubuntu without deleting the WIndows7 partition ?

---

### Post by kiranvinayan on 2013-11-28
Find Disk Utility and 'sudo fdisk -l' screenshots attached.

---

### Post by fantab on 2013-11-28
> **kiranvinayan said:**
> Laptop: ASUS X550C-X0029D
The laptop came with just DOS. I installed Windows 7 Ultimate(64 bit) and deleted all the partitions and created a 100GB parition for Windows. Then I used EASEUS parition manager and created a 300GB NTFS parition. **[COLOR=#b22222]There is a 100MB GPT parition also[/COLOR]**.
When I tried to install Ubuntu 12.04.3, the installer does not detect Windows 7. When I tried to create the partition for Ubuntu manually, it shows the hard disk without any of the exisiting paritions.

How can I install Ubuntu without deleting the WIndows7 partition ?

Did you change the Partition table from GPT to 'msdos'?
If you had GPT originally then you wll have UEFI boot. Check in BIOS/UEFI under 'Boot' and tell use what you see. You would see something like, UEFI/EFI or Legacy/CSM or Auto.

To cut to the chase, to be able to install Ubuntu you will have remove that 100Mb GPT partition, if you can. And/Or use [**FIXPARTS**]("http://www.rodsbooks.com/fixparts/") to remove that GPT backup data. Then you'll be able to install Ubuntu.

However, if I were you, I would re-convert my HDD to GPT and install both Windows and Ubuntu in UEFI mode.
GPT and UEFI have replaced 'msdos' and BIOS respectively. BIOS and 'msdos' are more than thirty years old and have limitations with newer hardware and are being phased out in favor of UEFI and GPT.
[Advantages of GPT]("https://wiki.archlinux.org/index.php/GUID_Partition_Table")
Advantages of UEFI:
[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)
[http://compreviews.about.com/od/motherboards/a/UEFI.htm](http://compreviews.about.com/od/motherboards/a/UEFI.htm)
[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Advantages](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Advantages)

Do consider UEFI and GPT. If you need further assistance then do ask.

Good Luck.

---

### Post by Bucky Ball on 2013-11-29
Please attach large screenshot using the paperclip icon in 'Go Advanced' rather than inserting in the body of posts. Spare a thought for those with slow connections or vision issues. Thanks. I have attached these one for you.

Incidentally, it is 'gksudo' for a GUI as root, for instance:

```
gksudo gparted
```

---

### Post by kiranvinayan on 2013-11-29
I followed the instructions in the following thread and was able to solve the problem - [http://ubuntuforums.org/showthread.php?t=1604074&page=4&p=10022223#post10022223](http://ubuntuforums.org/showthread.php?t=1604074&page=4&p=10022223#post10022223)

---

