---
title: "dual booting"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by lawlor59 on 2010-12-01
I had Vista on my laptop and then started dual booting with windows 7 last week. downloaded ubuntu today and installed but just not feeling it. i have looked in add remove programs but its not there. can someone point me in the right direction. How do i remove ubuntu including the grub screen and free the space up on the hard disk because i'm missing 25gb. any help is greatly appreciated

---

### Post by garvinrick4 on 2010-12-01
Did you download a install of Ubuntu called Wubi? If so then look right next to Users in C; drive and you will see a folder called Ubuntu open it and double click on uninstall.
After that go into command line in Windows and:
```
bcdedit
```
and make sure nothing in there with wubildr:
If so post back.

---

### Post by lawlor59 on 2010-12-01
no it was ubuntu-10.10-desktop-i386. i installed from the boot menu to a partition. i can't find ubuntu files on my computer. i have a acronis backup image of my machine would this work because i didnt want to try and mess everything up because the grub menu.

---

### Post by oldfred on 2010-12-01
You first need to reinstall the windows boot loader to the MBR. Then with gparted you can delete the Ubuntu partitions. Then from windows MMC you can expand your windows into the free space.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by garvinrick4 on 2010-12-01
#You will have to use a linux or windows partitioning tool to reformat to NTFS and enlarge the windows partition to use up the empty space left by Linux's 25 gig. There is gparted 
in linux and Windows has its own. Google which ever one you use and read up on instructions. Be careful and have backups anytime you fool with your drive something
can go amiss. 
#If you can take a screen shot of gparted and post here with attachment tool you will get
some help.
#oldfred has already given you some guides I see, very good.

---

