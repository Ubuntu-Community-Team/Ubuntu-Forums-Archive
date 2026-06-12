---
title: "Ubuntu Dual Boot Windows 7"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by w33t on 2011-06-18
So what im trying to do is install windows 7 on my computer that is already running ubuntu 10.10. i love ubuntu dearly and i dont want to get rid of it but i need this computer for gaming and playonlinux is only going so far. so my questions:

1.) how would i go about partitioning my hard drive and installing windows 7. i have a copy of windows already and i have a basic knowledge of the bash shell and feel moderately comfortable using it. still learning though.

2.) my computer is a mac. i dont know if that is going to matter much, i assume it wouldnt but i thought id put it here just in case. i got a macbook pro about a year ago and it took me about 2 weeks to realise that it wasnt the os that i wanted to use. i completely wiped the machine and installed 10.10. so. apple hardware completely ubuntu. 

any help or tutorials that you could point me to would be very helpful. i know a lot about this distro but ive never had to partition on linux before.

---

### Post by Frogs Hair on 2011-06-18
See the section on Windows after Ubuntu at the link . [https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

---

### Post by oldfred on 2011-06-18
I do not know Macs but it is a problem. Macs use the new gpt partitioning and windows only works with MBR partitioning. Windows 64 will work with UEFI but Macs use a EFI that is part EFI & part UEFI. 

Mac then created a hybrid part MBR, part gpt that is fragile but works. You have to have windows in the first 4 or primary partitions. Windows has to have a primary NTFS partition with the boot flag.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by srs5694 on 2011-06-18
If you were setting it up from scratch, the best way to do what you want is to set up both OSes on an MBR-only hard disk using the Mac's BIOS compatibility mode. That way it'll be much like a regular PC, and you won't have EFI or GPT issues to deal with. (EFI and GPT both have advantages, but Windows on a Mac ties your hands and creates disadvantages to both.)

I recommend you download and run the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) then post the RESULTS.TXT file that it creates, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to keep it legible. That output will tell us how your disk is currently partitioned, which will enable us to better advise you on how to proceed.

---

