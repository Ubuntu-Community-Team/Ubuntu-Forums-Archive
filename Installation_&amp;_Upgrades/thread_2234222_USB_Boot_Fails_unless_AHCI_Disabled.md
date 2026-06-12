---
title: "USB Boot Fails unless AHCI Disabled"
date: 2014-07-13
forum: Installation &amp; Upgrades
---

### Post by Scott_Saccone on 2014-07-13
My problem was that when I tried booting Ubuntu 14.04 from a USB stick, I got (via pressing ESC) several messages like "grep: /root/cdrom/preseed/ubuntu.seed: No such file or directory" and the boot fails. I discovered that changing the "SATA Operation" option from "AHCI" to "Disabled" in the BIOS seems to allow a normal USB boot.

The hardware is a new Dell Latitude E7440 laptop with Ubuntu 12.04 LTS pre-installed on the SSD. The SATA options in the BIOS are AHCI/RAID On/Disabled. I installed Ubuntu 14.04 on a USB stick using the Pendrive tool (was considering using it to resize the SSD Ubuntu partition).

When SATA is set to AHCI in the BIOS the USB boot fails in a very strange way. After several "no such file" messages, there's a message "Using CD-ROM mount point /cdrom/" followed by "scanning disk for index files" after which it seems to find an Ubuntu 12.04 installation. Then it seems to run the Dell Recovery tool, which came preinstalled on a special SSD partition. The recovery tool then fails with some message like "only for Dell machines." _It's strange the USB boot would boot any partition it finds on the SSD without asking_. Is this a security concern?

When SATA is set to "RAID On" in the BIOS, the USB boot hangs on the screen with the Ubuntu logo and the little moving dots.

When SATA is set to AHCI, the pre-installed Ubuntu boots normally from the SSD.

Why does the USB boot fail with AHCI? What are the consequences of disabling AHCI? Does this mean Ubuntu 14.04 is generally not compatible with this hardware yet? Comments appreciated.

---

### Post by oldfred on 2014-07-13
While not exactly your model it discusses some issues that seem to apply to all Intel chips? Or may just the way Dell configures systems?
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

My old systems could only boot XP with AHCI off, but Ubuntu worked with it on. And supposedly you need AHCI on for trim to work with SSD. Do not turn RAID on as that may write RAID data to drive and cause further issues.

---

