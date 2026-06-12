---
title: "WinXP - install after Linux?"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by OMRebel on 2006-04-06
Okay guys, I'm running Breezy, but because of some classes I'm taking, I've got to install XP on my machine.  I have a laptop with only one drive on it that is currently running Breezy.  Is it possibly to repartition the drive and install XP on that partition, without screwing up my Breezy install?  Or, would I be better off just backing up my home directory, wiping everything clean, and installing XP and then Breezy?

Thanks.

---

### Post by aysiu on 2006-04-06
Windows generally likes being at the beginning of the drive, so put it there.

It also takes over the MBR, so you'll have to reinstall Grub afterwards:

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

### Post by OMRebel on 2006-04-06
Thanks aysiu.  Is there a HowTo on repartitioning a drive in Ubuntu?

---

### Post by aysiu on 2006-04-06
[QUOTE=OMRebel]Thanks aysiu.  Is there a HowTo on repartitioning a drive in Ubuntu?[/QUOTE] You need a live CD. Personally, I recommend [using PCLinuxOS's DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142). You can also use Knoppix's QTParted. If you have a Ubuntu live CD, you can "install" GParted on it and use that.

All (DiskDrake, QTParted, and GParted) are graphical partitioning programs and are pretty easy to figure out.

---

### Post by OMRebel on 2006-04-06
Cool.  Thanks again!

---

