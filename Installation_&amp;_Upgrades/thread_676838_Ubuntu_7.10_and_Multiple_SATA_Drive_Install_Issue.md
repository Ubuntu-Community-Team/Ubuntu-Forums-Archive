---
title: "Ubuntu 7.10 and Multiple SATA Drive Install Issue"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by mevans336 on 2008-01-24
Hello all,

I have installed Ubuntu 7.10 onto my machine, but when I boot I get a Grub Error 17. I've read the link here [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17) but I have a quick question which I think will resolve my issue.

When Ubuntu installed, I noticed it installed the grub MBR to hd0, which appears to be my PATA disk. I have 4 SATA hard drives, 1 PATA hard drive, 1 SATA DVD-ROM and 1 PATA CDRW. My BIOS is set to boot off the 1st SATA disk which holds my Vista install. I think if I re-install Ubuntu and tell it to write the Grub MBR to the 1st SATA disk, all should be fine and I'll even be able to dual-boot. If so, looking at the screenshot I've attached from gparted, /dev/sdd is where Ubuntu is installed and /dev/sdc is where I'd like the grub MBR to go. (/dev/sda and /dev/sdb are an nvraid/fakeraid RAID scratch partition, although that might throw a wrench in my plan?)

If that won't work, I'm perfectly happy to install everything, including the grub MBR to /dev/sdd and use my BIOS boot-order key to choose Vista or Ubuntu.

So, I guess my question is, where should I tell grub to install if I want it to write the MBR to /dev/sdc (hd3?) or /dev/sdd (hd4?).

Thanks!

---

### Post by njparton on 2008-01-24
I also have several HDDs (a mixture of PATA and SATA too).

During install I unplug all hardrives apart from the one I want to install ubuntu to, plug them back in afterwards and then update fstab.

I too also use the bios boot menu to control booting between ubnutu and vista.

It's just the simplest and safest way to do it.

---

