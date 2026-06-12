---
title: "Install problems on Averatec 3200"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by msfisher on 2010-03-28
I haven't been on the forum for a while simply because things have been working well.

Until now.

After MANY attempts to find a distro that would install to my Averatec 3200, I got PCLinuxOS 2009.2 to run.  At the time, I'd tried several versions of Ubuntu, none of which would even load to the Live CD stage.  I suppose I should have been happy and left well enough alone, but when both Ubuntu 10 came out and PCLOS2010, I decided to update the latter and try out the former.  Big mistake.  PCLOS trashed my MBR when I tried to install it.  Both Lucid and U9.10 will load to the live desktop, but neither one will install.  Both versions -- and variants such as Kubuntu and Mint8 -- get to about 15% on the file copy part of the install, then stop cold.  I've run into similar problems at various times with other distros.

I've managed to get some other Live CD's to run, and one of them -- PartedMagic -- I think gives a hint to at least part of the problem.  Parted Magic won't load or run with Xorg.  It requires Xvesa.  FYI, PC Wizard and other tools report the following:

  > Manufacturer : AVERATEC
  > Mainboard : AVERATEC 3200
  > Chipset : VIA KM400
  > Processor : AMD Athlon XP-M @ 1533 MHz
  > Physical Memory : 1024 MB (1 x 1024 DDR-SDRAM )
  > Video Card : VIA/S3G UniChrome Graphics
  > Hard Disk : IC25N040ATMR04-0 (40 GB)
  > DVD-Rom Drive : QSI CDRW/DVD SBW-242
  > Network Card : Broadcom BCM43XX
  > Network Card : VIA Rhine II

Since I can get versions 9 & 10 to boot to a live desktop, I'm very uncertain as to whether the graphics are the problem.

So, question: what else could it be?  

More FYI: on install, I set the partition file system to ext3 (should I stick with 2?) and the mount point to root.

Also, please note that I got exactly ONE distro to run -- PCLOS2009.2.  I tried all of the major distros and some minor ones before this worked.  What did that distro do different from Ubuntu which let it install and run?

Thanks in advance for any help!!

---

