---
title: "Problem with SATA -Installation"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by klemi on 2007-01-05
Hallo I have big Problem,
My Hardware is:
Gigabyte 965P-DQ6 Mainboard with INTEL chipset 965/ICH8
Samsung 400 MB SATA II
In BIOS I have selected AHCI-Mode.

I start with ubuntu Live CD but it cannot dedected my hard disk.
I start with the non-graphic-Mode. For my Hardware it will install some driver, but I unknown waht I must select. The driver ahci was not effected to dedect the hard disk.

With the new knoppix CD 5.1 I can make a partition of my hard disk.Knoppix dedects the hard disk  This CD has Kernel version 2.6.19.
Are  any problems with kernel 2.6.17 in Ubuntu Live CD?

Wath can I do? Can you help me?

Please ......

Klemi

---

### Post by mikeyandmary on 2007-01-05
I saw this while I was wandering through the forums. I think it might be similar to your problem...

[http://www.ubuntuforums.org/showthread.php?t=234706&highlight=JMicron]("http://www.ubuntuforums.org/showthread.php?t=234706&highlight=JMicron")


Hope you find a solution...

---

### Post by cronholio on 2007-01-05
I guess you mean a 400 GB disk. I just bought one of these (Samsung 400 Gig SATA II) and it isn't recognized by my Edgy installation. I'm trying to fix it and I'll post here if I find a solution.

---

### Post by cronholio on 2007-01-05
Great success! :D

Behold the power of the "Run SATA-II in IDE mode" BIOS setting. I can see the disk now. Check in your BIOS setup if you have a similar setting and enable it for this disk.

By the way, I have no clue if the max throughput speed will be low (as for P-ATA) when this is enabled. Does anybody know?

---

### Post by logos34 on 2007-01-05
Have either of you tried setting the disks for sata 150MB/s mode?  (you know, take the jumper off or put it on--can't remember which).  Just a thought...probably won't make a diff, but hey worth a try.  

> have no clue if the max throughput speed will be low (as for P-ATA) when this is enabled.

if it makes you feel any better, even if it does run as ata6 (133MB/s) or ata5 (100MB/s) you won't notice the diff compared with sata II (300MB/s)--those are just theoretical max burst speeds that the interface is capable of (i.e. for a split second).  Overall performance is remarkably similar.  You'll get an average read write speed for a 7200rpm disk in the 50-65MB range no matter whether its pata or sataII.

---

### Post by kebes on 2007-01-05
There are well-documented problems with the Intel 965 chipset and any kernel that is 2.6.17 or older (which unfortunately includes Edgy). Many details and suggestions can be found here:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

For many people passing boot parameters to the kernel fixes the problem and they can install properly. (Boot flags like "all-generic-ide pci=nommconf noapic" and so on... refer to the link above.)

Others have found that it was not possible to install Edgy, but Fedora Core 6 and OpenSUSE 10.2 installed properly (since they use the 2.6.18 kernel).

My recommendation is to read the above link carefully. It lists your motherboard and several possible fixes. The exact fix depends on your setup (are you installing from an IDE CD-ROM to a SATA hard drive? etc.) Post more information if you get further along. Remember that during installation you can use "Ctrl+Alt+F1" (and F2, F3, etc.) to get access to behind-the-scenes kernel errors that may be useful.

Good luck.

---

