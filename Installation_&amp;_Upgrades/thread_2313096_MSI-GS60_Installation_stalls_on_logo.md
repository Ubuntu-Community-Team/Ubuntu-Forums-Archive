---
title: "MSI-GS60: Installation stalls on logo"
date: 2016-02-09
forum: Installation &amp; Upgrades
---

### Post by chris2132 on 2016-02-09
I have tried searching through the forum and still no luck. 

I got a MSI GS60 Ghost Pro-002 I am trying to install Ubuntu on. 

Here are the specs for the system:
[FONT=arial]6th Generation Intel® Skylake™ i7-6700HQ
[/FONT][FONT=arial]NVIDIA® GeForce™ GTX 970M
[/FONT][FONT=arial]16GB (2x8GB DIMMS) DDR4 2400MHz
[/FONT][FONT=arial]256GB Samsung 950 Pro M.2 NVMe PCIe SSD
[/FONT][FONT=arial]256GB Samsung 850 Pro [/FONT]SATA III Internal SSD 


I'm trying to install ubuntu on the 950 and windows on the 850. 

I've tried installing both 14.04 and 15.10 using usb and they both get to the initial ubuntu screen and stall. 

As far as BIOS goes.  I have updated the bios. Turned off secureBoot and fast start, switched from legacy to UEFI both with and without CSM. 

If anyone can help, I would greatly appreciate it!

---

### Post by oldfred on 2016-02-09
Another thread on similar machine, but RAID which adds more complexity.
 MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)

Both Skylake & nVidia add some issues.
Are you using nomodeset, or is system booting with Intel video, not nVidia?

You do need newest version of Ubuntu to have new kernel & support software. Intel also has newer files for Skylake.

 Skylake needs this boot parameter:  i915.preliminary_hw_support=1, May not be needed with newest drivers/kernels or you may just need nomodeset.
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by maraym on 2016-02-09
Different system, but I'm wondering if you're having the same problem as me [http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)

After the stall, try Ctrl-Alt-F1 to see if you're getting similar errors to me

---

### Post by oldfred on 2016-02-10
Someone with a gs40 commented on this thread that he has it working but only for a few hours.

[http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work](http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work)

---

