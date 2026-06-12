---
title: "Ubuntu Hoary won't see my SATA drive for installation"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by princemackenzie on 2005-09-10
Hello all, I was looking for some help with this.

I am trying to put ubuntu onto my hot new X64 machine -

Specs are:
MSI RS480M2-IL
Venice 3000+
Silicon Image 3112 SATA controller
Samsung 160 GB SATA drive.

it's a single drive, not RAID or anything.  Anyway, I can not get the installer to see the drive - it only sees the PATA drive i use for storage when I get to the partitioning screen.

I really want to put ubuntu on my new machine, but how can get the installer to see my SATA drive?

---

### Post by Daniel G. Taylor on 2005-09-10
It looks like support for that SATA chipset was a bit experimental when Hoary was released, see:
[http://linuxmafia.com/faq/Hardware/sata.html#siliconimage](http://linuxmafia.com/faq/Hardware/sata.html#siliconimage)

The next version of Ubuntu (called Breezy) has just had a [preview release](http://releases.ubuntu.com/breezy/) put out, perhaps you might fare better trying it? You may want to wait for the final release in a month though. I was able to install Breezy without any problems on my VIA VT6420 SATA controller.

---

### Post by netneo on 2005-09-17
Hi everyone

Even i seem to facing the same problem with SATA drive

My system is:
Processor---->AMD Athlon A64 3000+ having Socket 939
Motherboard----->MSI RS480 with ATI x300 Onboard gfx
Ram------>512 Mb DDR
Hard Disk----->Samsung 80 Gb SATA

I had installed WinXp with NTFS and 3 partitions of sizes 29.2,29.2 and 15.9 gb respectively

Has anyone tried out what one person has suggested--to try and change BIOS settings of SATA drive from Combination to Normal?

Will it work for our systems as well?

Should be doing this without my WinXP getting affected?

This wont affect the GRUB loader will it?

Have any of you faced any problems with Hoary 5.04 after that?

Thank you

---

