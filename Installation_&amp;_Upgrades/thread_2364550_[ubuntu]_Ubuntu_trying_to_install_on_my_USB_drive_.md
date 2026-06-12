---
title: "[ubuntu] Ubuntu trying to install on my USB drive instead of my hard drive"
date: 2017-06-24
forum: Installation &amp; Upgrades
---

### Post by quipbip123 on 2017-06-24
I am trying to install Ubuntu on my laptop off of a USB drive, but ubuntu keeps trying to install on the USB rather than the hard drive. 

When I try installing it using a 4GB usb, I get an error saying that there is not enough memory because my computer has only 4GB of space, but ubuntu requires 8GB. 

When I try installing it using a 16GB USB drive, one of two problems occurs

1) I get past the space limitation, but I get stuck at the "installation type" menu. If I click "install now", I get the message "no root file system is defined; please correct this from the partitioning menu". If I click "+", "-", or "change", I get the following error:

[http://i.imgur.com/wZWEiAf.png](http://i.imgur.com/wZWEiAf.png)
[http://i.imgur.com/3epLudB.png](http://i.imgur.com/3epLudB.png)
[http://i.imgur.com/mavRJhi.png](http://i.imgur.com/mavRJhi.png)

2) I get a warning that says "Error fsyncing/closing/dev/sda1: input/output error". If I click ignore, I repeatedly get the same error with sda2 through sda5 and the sda without a number. After all of those, even more warnings/errors popup (see screenshots below). I get to selecting the timezone and creating a user account, and the installation starts, but it does not ever finish.

[http://i.imgur.com/CsIButT.png](http://i.imgur.com/CsIButT.png)
[http://i.imgur.com/fBUxemt.png](http://i.imgur.com/fBUxemt.png)
[http://i.imgur.com/zzd1IKe.png](http://i.imgur.com/zzd1IKe.png)

Here is information about my laptop:
Model: Acer Aspire E1
RAM: 4096 MB
I don't know how much memory the hard drive has because I have no operating system installed right now and don't know how to check

I have safeboot disabled, and I have AHCI mode enabled in the BIOS settings.

Do you guys know what the issue could be?

---

### Post by yancek on 2017-06-24
One of your images shows that you have an EFI (ESP) partition.  Do you or did you have another operating system installed?  If you do have another OS, what is it?  Do you have any unallocated space on the drive on which to install Ubuntu?  If you do have another OS such as windows 8 or 10, did you turn off fastboot and hibernation?  If you have a newer (8 or 10) windows, you might take a look at the link below which is the Ubuntu documentation for dual-booting UEFI.  If you don't have another OS, let us know.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by quipbip123 on 2017-06-24
I don't have another OS installed. This is my brother's old laptop, and he removed Windows 8 from it years ago.

---

### Post by ubfan1 on 2017-06-24
Check that the firmware on that machine is current.  Acers might need to have a supervisor password set before showing other UEFI options in the UEFI settings (formerly known as BIOS).   Then you will need to set "trust" on the Ubuntu bootloaders when they get installed.  Is the disk without partitions, or is it still full of old ntfs formatted ones?  a UEFI boot requires an EFI partition (300M, FAT).  Then a root and swap partition minimum, optionally add a data partition if you like.

---

### Post by yancek on 2017-06-24
And the answers to the other questions?  Booting Ubuntu and selecting the Try Ubuntu option and opening a termnal and running:  sudo fdisk -l and posting the output here would be  start.

---

