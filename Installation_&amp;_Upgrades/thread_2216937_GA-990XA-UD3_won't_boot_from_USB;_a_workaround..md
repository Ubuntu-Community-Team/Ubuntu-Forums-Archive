---
title: "GA-990XA-UD3 won't boot from USB; a workaround."
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by MIJ-VI on 2014-04-14
**Problem:**

The GA-990XA-UD3 (rev. 1.x), and some other Gigabyte motherboards, won't boot from a fat32 USB flash drive formatted by gparted or Disk Utility but WILL boot from a flash drive formatted under Windows 7.

**A workaround** (aside from formatting the USB drive in Windows)**:**

Format the USB flash drive to ext4 and use UNetBootin to turn the drive into a means of installing Ubuntu etc via the GA-990XA-UD3's USB 2.0 ports. The USB 3.0 ports (Etron Technology, Inc., EJ168 USB 3.0 Host Controller), though otherwise bootable, wouldn't boot from a flash drive prepared in this manner.

The flash drive in question:

16GB Supersonic Xpress USB 3.0 Flash Drive (PSF16GXPUSB) 
[http://www.patriotmemory.com/product/detail.jsp?prodline=7&catid=92&prodgroupid=214&id=1088&type=23](http://www.patriotmemory.com/product/detail.jsp?prodline=7&catid=92&prodgroupid=214&id=1088&type=23) 
 
(Output from lsusb): 
Bus 001 Device 005: ID 13fe:5000 Kingston Technology Company Inc.

--

I'd like to thank the participants of the following thread for doing all the heavy lifting re establishing the futility of attempting to boot some Gigabyte motherboards from a USB flash drive formatted to fat32 by gparted or Disk Utility:

[all variants] Boot Error from USB 
[http://ubuntuforums.org/showthread.php?t=1712675](http://ubuntuforums.org/showthread.php?t=1712675)

---

