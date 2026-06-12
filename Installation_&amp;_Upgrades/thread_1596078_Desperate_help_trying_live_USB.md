---
title: "Desperate help trying live USB"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by BKbroila on 2010-10-13
Note: my OS is win7
I've got the usb-creator.exe and the iso on my desktop, and I've been trying to figure out how to make my USB flash drive a LIVE USB to just try ubuntu 10.10.
Where should those files be located when trying to make the live USB? Should they be on the flash drive, and/or my laptop? I've read guides online, but I feel like an idiot because I can't understand what to do.... 
And if I make my USB into a live one, will that be permanent? Also, do I have to partition the flash drive?
Thanks

---

### Post by wilee-nilee on 2010-10-13
Even though this is the second thread on the same subject I will reply.;)

The installer will read the ISO you have downloaded, to load the thumb. As another person suggested you might try unetbootin.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

So you start with a thumb freshly formatted to fat or fat32. The only thing that will be loaded to the thumb is the ISO using the installer, whether you use the one that came with the download or unetbootin. The installer is not made to run from inside the thumb, but to load the thumb.

If you get the thumb loaded and are able to boot you might want to give us a screenshot of gparted, the partitioner on the live cd. I suggest this not knowing your knowledge on resizing partitions or how many can actualy fit on a HD. You can also post a snippet of the W7 disc manager as well, or instead of gparted.

---

### Post by VMC on 2010-10-13
> **BKbroila said:**
> Note: my OS is win7
I've got the usb-creator.exe and the iso on my desktop, and I've been trying to figure out how to make my USB flash drive a LIVE USB to just try ubuntu 10.10.
Where should those files be located when trying to make the live USB? Should they be on the flash drive, and/or my laptop? I've read guides online, but I feel like an idiot because I can't understand what to do.... 
And if I make my USB into a live one, will that be permanent? Also, do I have to partition the flash drive?
Thanks

I'm not sure which "usb-creator.exe" you have, there seems to be several around. Is it this [one]("http://www.pendrivelinux.com/linux-live-usb-creator/")? If so just follow instructions once you run the program. By the way, I have used that LiLi usb creator before with success. What it creates is a Live USB that you can use to install your Ubuntu OS. There is a way to install Ubuntu onto a USB, but that's a different story. I'm guessing you want to install to your hard drive.

Do you have a cd/dvd burner?

---

### Post by efflandt on 2010-10-13
syslinux changed in 10.10 and some USB installers might not support that yet.  But creating a 10.10 bootable USB iso works from 10.10.  So maybe the most reliable way to do that if you do not have a running 10.10 system would be to burn a 10.10 CD, boot to a live system on it, then use Startup Disk Creator in that to make a bootable USB from the iso you have in your Win7 partition.

Since the Startup Disk Creator just creates a bootable live/install system on USB, it is not all that secure (auto logs in a user ubuntu who can do most anything) and may not take kindly to updates (since things that initially boot like the kernel will not update on it).

Startup Disk Creator installs on a common FAT32 file system.  But make sure you have the proper device, and if you format it from there, make sure you select the partition (with 1 in it), and not the entire flash drive (without a number) or that would mess up the partition table and not work.

Instead of that, a regular install can be done to USB flash using grub and a Linux file system.  It will work on 4 GB, but 8 GB or larger is recommended.  But you have to make sure that it installs grub to the USB drive and not the mbr of your internal drive.

---

