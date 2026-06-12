---
title: "Error 15 in consequence of installation"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Aiolos on 2008-05-06
Am running Windows 2000 Pro on two IDE HDD (not arrayed in RAID), Soyo SY-K7V Dragon Plus MB, with 768 MB DDR.  HDa has 1 primary partition and 1 extended partition that comprises 6 logical partitions.   HDb has 1 primary partition and 1 extended partition that comprises 2 logical partitions.  All partitions formatted NTFS.  

Downloaded, verified hash, and burned Ubuntu-8.04-desktop-i386.iso to CD.  Have read instructions at [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html), and booted from same CD. Was unable to discover Wubi option from opening menu.  Initiated &#8216;Ubuntu Install&#8217;, but, remembering very spare instructions on partitioning at foregoing link, aborted installation upon seeing Ubuntu commandeer my HDD.

Wiped and checkeddisk  F:\

Downloaded Wubi-8.04.exe to F:\wubi, again devoid of any Windows-based files. Wubi  then downloaded Ubuntu-8.04-desktop-i386.iso anew to F:\wubi and verified.  Ubuntu proceeded to download/install full complement of files, after which I was made to reboot. Choosing Ubuntu from &#8216;dual-boot screen&#8217;, I observed Ubuntu set up housekeeping, ultimately requiring another reboot.  

On the second reboot the following error condition was produced.

Filessytem type is ntfs, partition type 0x7
Kernel   /boot/vmlinuz-2.6.24-16-generic root-uuid-60A4C7C3A4C799C4
loopp=/ubuntu    error 15:file not found

ESCaping out, I was presented with following menu:

Grub4dos 0.4.3 2008-04-22, memory:639K/766M, codeend:0x41228
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, memtest 86+
Other operating systems:
 Windows 2000 Professional

None of the foregoing menu options was functional.  When attempting to boot Win 2K Pro, the following error message was produced:

Booting microsoft windows 2000 professional  root (hd1,0)   error 17 cannot mount selected partition  press any key to continue.

Pressing any key to continue looped me back inescapably to the foregoing menu.  I had to punch out.

I return to instructions at [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html) for Dual booting Windows and Ubuntu, and Manually editing partition table options.  Somebody please explain why 1) Resizing existing Windows partition; 2) Creating swap partition; 3) Creating root partition; and 4) Creating a separate home partition, presumably at HDa-4, a.k.a., F:\, will not jeopardize preexisting NTFS partitions on which Win 2K Pro and all Windows apps depend, not to mention my hierarchy of work files positioned at  HDa-7, a.k.a., I:\.

Do not see how to proceed safely.  Assume my work is backed up to the minute.  I do not wish to reinstall anything.

Thanks in advance.

---

### Post by Pumalite on 2008-05-06
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

