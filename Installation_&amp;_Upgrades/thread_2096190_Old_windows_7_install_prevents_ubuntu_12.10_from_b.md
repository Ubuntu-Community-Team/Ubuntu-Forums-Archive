---
title: "Old windows 7 install prevents ubuntu 12.10 from booting"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by morgendorffer on 2012-12-19
Since i was having trouble with windows 7 on a computer I tried to replace it with ubuntu. Im a newb when it comes to linux but not useless on computers in general. I used an ubuntu cd and the test option, wiped the old windows harddrive. i thought that at least; i deleted the partition, created a few new for ubuntu and other stuff. Then i installed ubuntu on one of them and it came to the restart computer phase. I removed the cd when it told me to and restarted.

When it started the computer again, it said "could not find windows 7, insert repair disc" or somesuch. The disk where win7 was was completely wiped afaik, s i have no idea why it would know it had ever been there. I could not get past thar screen at all and now im at  a loss at what to do. Anyone know what i did wrong? Thanks.

Ps sorry for bad language, swede typing on phone xD

---

### Post by hanzukun on 2012-12-19
Sounds like you didn't install the bootloader for Ubuntu, ie GRUB. It is the very first "program" located on the very beginning of the harddisk. Since it is asking you to insert the windows dvd, the windows bootloader must still be there trying to boot windows.

Boot the Ubuntu CD again, I think there is a "recovery mode" there as well, but I have never tried it. Otherwise, reinstall Ubuntu again and make sure you also install GRUB, which it asks for in the end.

---

### Post by DMaretta on 2012-12-19
Usually a repair disc will retrieve Win7 system information from a partition that can't be reached from Windows. When installing Ubuntu, try to find this particular partition and erase it before creating those for Ubuntu. Compare the total size of the disc that is informed in the computer documentation to the space you are using for your partitions. If the difference is of about 400 to 500Mb there is still a partition to delete before installation.

---

### Post by Wim Sturkenboom on 2012-12-19
Does your system has an UEFI bios? If so, do some research on that. I had a similar problem on a new system (always booted to windows), till I found out about UEFI.

There are some threads here on the forum and often there is a reference to Yannbuntu's boot-repair software.

This is the thread that got meon the right track: [http://ubuntuforums.org/showthread.php?t=1974392&highlight=uefi](http://ubuntuforums.org/showthread.php?t=1974392&highlight=uefi)

---

