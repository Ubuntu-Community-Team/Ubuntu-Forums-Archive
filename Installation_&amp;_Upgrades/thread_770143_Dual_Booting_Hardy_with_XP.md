---
title: "Dual Booting Hardy with XP"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by tommyhakinen on 2008-04-27
I have been using Gutsy for a month on my laptop. I want to dual boot my dekstop with XP and Hardy. I have two partitions. One partition, I have already had XP installed. The second one was left for my Hardy. I wanted to know if I install Hardy on the second partition, will it affect my current XP installation? I was trying the live cd and it seemed to detect both of my partitions and only allowed me to install on the freed space which is the second partition. Next question is, will it devide my second partition into the default partition of Ubuntu installation(which has three partitions)?

Thank you

Regards,

tommy

---

### Post by tommyhakinen on 2008-05-01
Okay. I have figured it out myself on how I dual boot XP with Hardy. Here I will explain my experience.

First I have 2 partitions on my hard drive. First partition is occupied by XP. My second partition which I left for Hardy was a free space. Then I boot the Hardy from the live cd. I went to the partition editor to change my second partition to ext3 then start the installation.

The installation seemed to detect my second partition and I used the whole partition for Hardy (Guided). After successfully installed Hardy, I realized that I had one extra partition (in linux native format) other than the defaults (the partition for the root and swap). It took about 500MB of my hard drive. I mounted and checked that extra partition. I contained Lost+Found. I was confused what caused that. Is there anyone know what caused that?

After I found out that, I wiped out the partitions containing Hardy and did a fresh installation manually. I successfully did it. But one thing I could not figure out. How do we determine the size of the swap partition?

Although I have successfully dual-bot XP and Hardy, I still had some problems that needs solution. Hope this can help those who are experiencing the same problem as me.

Thank you.

Regards,

tommy

---

### Post by ssican on 2008-05-02
How To Dual Boot - XP and Ubuntu:

1) [http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)

2) [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

EDIT 1:
Resizing a Windows Partition:
[http://www.easy-ubuntu-linux.com/resize-windows-partition.html](http://www.easy-ubuntu-linux.com/resize-windows-partition.html)

EDIT 2:
How to Partition:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Sillywombat on 2008-05-02
Number one is a good guide, simple with lots of little colourful pictures.
Cheers! :KS

---

