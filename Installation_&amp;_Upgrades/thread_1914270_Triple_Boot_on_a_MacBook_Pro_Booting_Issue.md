---
title: "Triple Boot on a MacBook Pro Booting Issue"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by wxyabc on 2012-01-24
Hello all,
This is my first post, so I hope this goes here. I'm having problems setting up my macbook pro to triple boot. I've taken the following steps:
1.) Starting with OSX Lion, use disk utility to create Windows, Ubuntu, and Swap partitions using FAT.
2.) Boot into Windows 7 install disk.
3.) Install Windows 7 on the corresponding partition.
(at this point everything is fine, no need for Bootcamp)
4.) Boot into Ubuntu 11.10 Install cd (set acpi off).
5.) Install Ubuntu 11.10 and swap partition on appropriate partitions.

At this point I can boot into MacOSX and Ubuntu. Upon trying to boot into Windows 7, I'm brought to the grun bootloader screen and selecting the windows 7 option leads to a Windows screen stating that there was an issue reading the boot config data. (Status: 0xc0000225) I tried using testdisk to repair the boot sector, but the backup matched the original boot sector. I then went into windows 7 install disk and ran Bootrec.exe to FixBoot and FixMbr from a command prompt. Now, booting from windows no longer shows grub, but the short and painful message: "Missing Operating System." Running "verify disk" from OSX disk utility, I get the message that the disk needs to be repartitioned and something about a lack of EFI.

Give it to me straight: do I have to do a clean reinstall of everything? I've already had to do this twice, but if there's a way for me to repair my partition table that'd be even better.

Thanks in advance, it's awesome to be posting here for the first time.

---

### Post by zvacet on 2012-01-24
I hope [https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool](https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool) wil work on Mac.After you repair grub boot in Ubuntu and run 

```
sudo update-grub
```

---

