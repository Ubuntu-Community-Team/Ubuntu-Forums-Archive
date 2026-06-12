---
title: "problem booting ubuntu with vista boot loader"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by Shardsofmetal on 2008-06-24
Because I wanted to dual-boot linux using Vista's boot manager instead of GRUB, I followed the instructions at [http://www.canerten.com/dual-boot-linux-and-windows-with-windows-boot-manager/](http://www.canerten.com/dual-boot-linux-and-windows-with-windows-boot-manager/). When I try to boot Ubuntu, I get the grub> prompt. I typed "find /boot/grub/stage1" and got the error file not found.

To create the boot file, I ran dd --list on Vista, and got:

```
rawwrite dd for windows version 0.5.
Written by John Newbigin <jn@it.swin.edu.au>
This program is covered by the GPL.  See copying.txt for details
Win32 Available Volume Information
\\.\Volume{8d752dd9-1a66-11dd-8da5-806e6f6e6963}\
  link to \\?\Device\HarddiskVolume1
  fixed media
  Not mounted

\\.\Volume{8d752dda-1a66-11dd-8da5-806e6f6e6963}\
  link to \\?\Device\HarddiskVolume2
  fixed media
  Mounted on \\.\c:

\\.\Volume{8d752ddf-1a66-11dd-8da5-806e6f6e6963}\
  link to \\?\Device\CdRom0
  CD-ROM
  Mounted on \\.\f:


NT Block Device Objects
\\?\Device\CdRom0
  size is 2147483647 bytes
\\?\Device\Harddisk0\Partition0
  link to \\?\Device\Harddisk0\DR0
  Fixed hard disk media. Block size = 512
  size is 320072933376 bytes
\\?\Device\Harddisk0\Partition1
  link to \\?\Device\HarddiskVolume1
  Fixed hard disk media. Block size = 512
  size is 10737418240 bytes
\\?\Device\Harddisk0\Partition2
  link to \\?\Device\HarddiskVolume2
\\?\Device\Harddisk0\Partition3
  link to \\?\Device\HarddiskVolume4
  Fixed hard disk media. Block size = 512
  size is 3806330880 bytes
\\?\Device\Harddisk0\Partition4
  link to \\?\Device\HarddiskVolume3
  Fixed hard disk media. Block size = 512
  size is 16096872960 bytes
```

I then ran the command "dd if=\\?\Device\HarddiskVolume3 of=linux.boot bs=512 count=1", and set up the boot menu item as described at the web page above.

Can anybody help me? Thanks a lot

---

### Post by logos34 on 2008-06-24
Try [EasyBCD.]("http://neosmart.net/wiki/display/EBCD/Linux")

---

### Post by Shardsofmetal on 2008-06-24
Thank you for that link, I installed that program and it makes it much easier to manage the Vista boot menu. However, I still have the problem that when it loads ubuntu, it goes to the grub> prompt. How do I boot ubuntu from there, or otherwise fix the problem?

---

### Post by logos34 on 2008-06-24
did you try Neogrub (method 2)?  what partition is linux?

---

