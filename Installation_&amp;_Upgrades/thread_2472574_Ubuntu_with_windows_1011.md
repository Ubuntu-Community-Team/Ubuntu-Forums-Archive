---
title: "Ubuntu with windows 10/11"
date: 2022-03-04
forum: Installation &amp; Upgrades
---

### Post by styleruk on 2022-03-04
Hi, I need a little help here.
So I have a new Dell laptop and it came with windows 11.  I immediately installed Ubuntu 20.04 and have predominately been using this, however, I have a terrible graphics issue with windows 11 and after much support from Dell and MS, it seems my only option is to try to install windows 10 (which does not have the issue on other laptops similar).   Sorry had to explain this first because I have a lot of scientific software on Windows 11 that takes an age to re-install, so what I did was make a new partition to put windows 10 on and try it out first before deleting windows 11, all whilst keeping Ubuntu of course.

Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048    493567    491520   240M EFI System
/dev/nvme0n1p2    493568    755711    262144   128M Microsoft reserved
/dev/nvme0n1p3    755712 279291903 278536192 132.8G Microsoft basic data
/dev/nvme0n1p4 495050752 497078271   2027520   990M Windows recovery environment
/dev/nvme0n1p5 497080320 500084735   3004416   1.4G Windows recovery environment
/dev/nvme0n1p6 338804736 495050751 156246016  74.5G Linux filesystem
/dev/nvme0n1p7 279291904 338804735  59512832  28.4G Microsoft basic data


So, one drive, 7 partitions.  

P3 is Windows 11
P4 is Winretools (whatever that is)
P6 is Ubuntu
P5 is a dell support partition
P7 is one I made to put windows 10 on.

I boot from a USB install for windows and start the install process in the hope to choose  P7 to install to, however, when I get to that bit in Windows install, it can't find any partition at all?  What am I doing wrong here?

---

### Post by breakdaze on 2022-03-04
Disclaimer, I have no experience with this.

1. Backup your system (Clonezilla, etc.)
2. Backup your data.
3. Consider using a virtual machine to test Windows 10.
4. try deleting the new partition, so it is unallocated space for the Win10 installer 
5. run Check disk on your existing partitions before continuing
6. Use custom configuration in Win 10 installer, point to unallocated space.
6.5 The Windows install will probably wipe out the grub boot loader, so be prepared to fix that later.
7. [https://www.xda-developers.com/dual-boot-windows-10-windows-11/](https://www.xda-developers.com/dual-boot-windows-10-windows-11/)

---

### Post by grahammechanical on 2022-03-04
I tried to find a tutorial on how to dual boot Windows 10 and 11 and found this one which says this

> Once you boot into the Windows 11 installer, click *Next, *and then *Install Now*. Setup will Start, and you should choose the *Custom* option. If you&#8217;re not seeing any drives, head into your PC&#8217;s BIOS and set the SATA controller to *compatibility/IDE/Standard Mode* for the drives to appear. Once that checks out, choose the partition that you&#8217;ve previously sized and labeled as *Windows 11 *and click *Next*. Windows will then install.

[https://www.digitaltrends.com/computing/how-to-dual-boot-windows-10-and-windows-11/](https://www.digitaltrends.com/computing/how-to-dual-boot-windows-10-and-windows-11/)

A Microsoft forum might be the better place to ask for help with installing Windows 10.

Regards

---

