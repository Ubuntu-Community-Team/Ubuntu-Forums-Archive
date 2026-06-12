---
title: "Reboot and Select Proper Boot Device after Install"
date: 2019-07-29
forum: Installation &amp; Upgrades
---

### Post by vp19 on 2019-07-29
Hello,

After installing Ubuntu, I can only boot through the boot menu, otherwise I get an error stating "Reboot and Select Proper Boot Device after Install." I have tried boot-repair among some other attempts to fix it. Here is the link from the first output: [http://paste.ubuntu.com/p/pdj4w2CdHj/](http://paste.ubuntu.com/p/pdj4w2CdHj/) . I tried to implement the recommended repair by following the instructions ([[FONT=arial]https://help.ubuntu.com/community/BootPartition[/FONT]]("https://help.ubuntu.com/community/BootPartition")) and created a partition for a separate /boot partition, but after running boot-repair again, it completes with an error. Here is the link for the output: [http://paste.ubuntu.com/p/Xg9k8QGDnZ/](http://paste.ubuntu.com/p/Xg9k8QGDnZ/) . I still have the same issue when booting. Any ideas on how to proceed? Any help would be much appreciated!

---

### Post by oldfred on 2019-07-29
If a Skylake system then it really is an UEFI based system.
But you  have installed in BIOS/MBR configuration which is the 1985 standard for DOS.
If new install,  you may want to reinstall in newer UEFI boot mode with gpt partitioning.

Issue probably is that system is set to boot in UEFI mode, sees you do not have that & posts error, but then tries BIOS mode as last resort. You may be able to change UEFI setting to BIOS only to eliminate warning message.

You also do not need /boot partition. That warning in Boot-Repair is for very old BIOS systems. Newer UEFI systems have yet to show that as an issue. I had asked Yann to suppress that message on newer UEFI systems & I thought he did, but now must have regression.
But better to use a smaller / (root) and then large /home and/or data partition(s). Even back with DOS, I used to add a d: drive for data and kept that for most Windows installs, and then Linux installs.

If you want UEFI info see link in my signature below.
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

      [/URL]
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr) 
    [URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by vp19 on 2019-08-01
Reinstalling in UEFI mode fixed the problem. Thank you!!

---

