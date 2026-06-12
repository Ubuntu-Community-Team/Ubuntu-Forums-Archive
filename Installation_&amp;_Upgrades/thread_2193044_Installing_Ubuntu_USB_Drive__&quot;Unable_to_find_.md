---
title: "Installing Ubuntu USB Drive  &quot;Unable to find a medium containing a live file system&quot;"
date: 2013-12-10
forum: Installation &amp; Upgrades
---

### Post by amartinson on 2013-12-10
Well I've spent the past 5 hours or so trying to get past this issue - I feel like my eyes are going to fall out! The error is "Busybox v1.18.5.... (initramfs) Unable to find a medium containing a life file system"

I've read up on a whole bunch on people who have experienced this problem, but have not personally found a fix that works for me.

So far I am tried three different ISO images (Xubuntu 12.10, 13.10 and Ubuntu 12.04), installed on two different flash drives (Sandisk 8GB and 32GB), with two different programs (LiLi USB Creator and Universal USB Installer).
I have tried many combinations of both USB 2.0 and 3.0 ports on my Mobo. I've tried messing with the BIO settings, booting with both Legacy and UEIF. I've tried messing with all the SATA settings in the BIOS.

I'm at a loss of where to go next. My MOBO is the Gigabyyte 990FXA-UD5.

Any ideas would be greatly appreciated! Thank you.

---

### Post by Bucky Ball on 2013-12-10
Welcome. Try Unetbootin. Silly question, but it is set in BIOS to boot from either CD or USB? Just asking ... ;)

Does this error occur immediately at boot or do you get to a menu which allows you to choose from kernels/other OS installs?

---

### Post by oldfred on 2013-12-11
I found this in my notes.

 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.

---

### Post by amartinson on 2013-12-11
That you for the replies. Bucky Ball, I have it set at the USB device is first boot order and I even tried the setting in the BIOS to mask the USB as a DVD.

oldfred, I will give that a shot. Is there an option in any of the USB creator programs to create a partition under 4GB or do I need to buy a smaller USB stick?

Also I will add that I got CentOS to boot up and install to a USB fine.

---

### Post by oldfred on 2013-12-11
I have not used an installer for ages, so do not know (I use grub2 and directly boot ISO) . 

I would think you could shrink the FAT32 partition. Windows only sees the first partition on a flash drive, but then still should work on that one.  Or any of the third party partition tools.

If you have a Linux install then you can use gparted to shrink it. Or use dd to install.

---

### Post by amartinson on 2013-12-11
After extensive searching I found a fix: [http://ubuntuforums.org/showthread.php?t=2143433&page=2&p=12871547#post12871547](http://ubuntuforums.org/showthread.php?t=2143433&page=2&p=12871547#post12871547)

Turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

On the bright side I am learning so much about computers. I learned about diskpart commands amongst much other things. :)

---

