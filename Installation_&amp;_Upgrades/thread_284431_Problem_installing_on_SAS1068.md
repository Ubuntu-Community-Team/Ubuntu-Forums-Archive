---
title: "Problem installing on SAS1068"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by eric.sperano on 2006-10-25
Hello everyone,

Here at work I have a HP Proliant DL-140. Months ago I succesfully installed Dapper on it with software raid.

Now i'm trying to use hardware raid. My controller is LSI Logic/Symbios Logic SAS1068 PCI-XFusion MPTSAS. I created a RAID-1 Array via the LSI bios at bootup. 

I then try to install daper with the desktop cd, it boots fine but partman hangs because he didn't detect any drive. 

By googling around I've found that I have to use the mptsas drivers. lsmod tells me that mptbase, mptsas and mptscsih are present. So it looks like dapper detects my controller but some how there are no hard drive attached to it. But i supposed they really are since i created a raid array.

I keep googling around but I don't find anything. I'm very familiar with linux but my usually I install it on a simple PC with a quite common IDE drive. First time I install it on a hardware RAID array. Never heard of SAS before. 

By searching, I've found some articles about fakeraid but I don't keven now if my SAS1068 is a fake raid or a real raid.

Thanks.

---

### Post by asg1290 on 2006-10-27
I'm having the same problem here on an HP xw9400 with a 1068.  Redhat 4 is able to see the drives but Ubuntu isn't.  The one curious thing I've noticed is that if I do an lspci I don't see the device at all!  Something isn't right with the kernel but it's beyond me to fix.  I've tried Dapper and Edgy and both fail to see the drive

---

### Post by asg1290 on 2006-11-10
Try turning ACPI Segmentation off in the bios and see how that goes, that fixed it for me

---

### Post by y.t on 2007-05-09
I have still the same problem on a hp xw9400 with ubuntu 7.04 x86_64. After installation the boot process is stopping with the grub screen. ACPI Segmentation is disabled.

---

### Post by kbyrd on 2007-11-02
I tried installing Gusty from the mini.iso this morning on an HP xw9400 with the LSI MPT SAS controller, same problem, frozen at "detecting disks". I'm running Debian with 2.6.22 on the box now, so that at least works. 

Help!

---

### Post by kbyrd on 2007-11-07
I'm having this problem still, but after looking at the dmesg output, I realize it's not the mpt drivers that are the problem. I'm getting an "oops" while modprobe is running, it looks like the ide_core driver. I started a nw thread here:
[http://ubuntuforums.org/showthread.php?t=606852](http://ubuntuforums.org/showthread.php?t=606852)

---

