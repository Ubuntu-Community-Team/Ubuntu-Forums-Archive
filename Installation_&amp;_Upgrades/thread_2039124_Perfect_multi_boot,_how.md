---
title: "Perfect multi boot, how?"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by pion33r on 2012-08-08
I got this 150 partition HD 25gb for xp 42977 MB for win7 and 90gb for my other files. now I plan to replace win 7 with linux so I go to advanced partition, during my installation but I got confused on how or what should i allocate on root (/) on swap and so on.... please help. thanks

---

### Post by 2F4U on 2012-08-08
What is the exact problem? Are you unsure about how large the partitions should be?

---

### Post by pion33r on 2012-08-08
> **2F4U said:**
> What is the exact problem? Are you unsure about how large the partitions should be?

the problem is I don't know how much mb/gb I should allocate on root, mount, swap ect...

---

### Post by mips on 2012-08-08
Very much personal choice on how you partition the free space.

Easiest option would be only two partitions, swap 1.5xRAM size and the rest as /

If you want a separate /home partition or more you would have to create an extended partition and put the other partitions in there as you are only allowed 4 normal partitions on a drive.

---

### Post by pion33r on 2012-08-08
> **mips said:**
> Very much personal choice on how you partition the free space.

Easiest option would be only two partitions, swap 1.5xRAM size and the rest as /

If you want a separate /home partition or more you would have to create an extended partition and put the other partitions in there as you are only allowed 4 normal partitions on a drive.


thank you so much. just one last question.
let say I will format everything.
does that mean that / or root is define as drive c in windows or the drive where the OS is installed and having a "home" is like having a drive d in windows???

---

### Post by oldfred on 2012-08-08
Linux is not Windows, so it is hard to relate Windows file structures to Linux. A /home is still part of the system as it has your user settings and program configurations and data files and all your data. You can in Linux also create additional data partitions like a D: drive in Windows and in fact if dual booting it is often best to have a shared NTFS data partition that will be d: in Windows and a data partition in Ubuntu. 

If you were dual booting with Windows, you do need to be careful on deleting the second install of Windows. Windows literally moves the boot files from a second install to the first install with the boot flag. And with XP first it reconfigures it to be a Windows 7 boot, so you have to repair the XP install to be able to boot XP.  So make sure your XP install disk works as a repairCD or make a Windows 7 repairCD before uninstalling as you can use that to repair XP.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by pion33r on 2012-08-09
thank to all the response.

---

