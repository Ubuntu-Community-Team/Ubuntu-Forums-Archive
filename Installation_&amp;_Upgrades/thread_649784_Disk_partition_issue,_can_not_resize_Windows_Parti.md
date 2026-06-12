---
title: "Disk partition issue, can not resize Windows Partition (Doing FromWindows-Install)"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by Zarok on 2007-12-25
Hello! I'm not exactly a Linux guru, but I know my way around computers and I've tried doing this for a good two days now and starting to run out of patience. I'm doing the installation on a IBM Thinkpad X30-laptop, which has no optical drive, nor do I have a USB optical for it, so I have to do it without a cd.


So. Originally I planned on doing the install from a USB stick, but I could never get it bootable, it just said no bootable partition on table. Tried Syslinux -s ,and I also tried, just out of curiosity, to make the stick MS-DoS bootable, and that wouldn't work either. Motherboard supports USB booting, so that's not the issue. Eventually I gave up on that, and decided to do the FromWindows-install. I did everything according to the FromWindows-guide, and eventually managed to boot into the alternate installer.

However, when I tried resizing the NTFS Windows-partition, it wouldn't budge. It just said partitioning drive, then screen went red and it said it can't resize the partition. I booted back to Windows, and tried it with Partition magic, and PM wouldn't even start, it gives a Error #117, Partition's drive letter cannot be identified. I ran PartitionInfo, first it says Disc Geometry Errors were detected on this drive , and when it starts, it has "Error #108: Partition didn't end on cylinder boundary. ucEndHead expected to be 239, not 22 " on the screen. Thus, I can't edit the partition size from Windows either.

I'm not exactly sure what the culprit here actually is. I'm thinking it could be some IBM recovery partition screwing the partition table up. However, I can't see any other partitions than the XP NTFS partition on PM nor the Ubuntu partition tool.



So, to sum it up. Can't resize NTFS partition in either Ubuntu nor XP. Wouldn't want to lose XP either, wanted to make the system dual boot. Questions:

A) Any way I could fix the resizing NTFS problem ? I have 20 gigs of free space on the NTFS drive which was supposed to be used for Ubuntu.

B) If I decided to give up on trying to save XP, is there any way I could even install Ubuntu anymore? Since I'm doing a FromWindows-install where the Grldr is loaded with boot.ini and the install is happening from a .ISO image on the HDD, wouldn't deleting the XP partition also delete the Ubuntu .ISO and end the install?

C) Any idea why my USB key boots don't work? Then I could do the bootup and install from the USB key. I tried using a .bat file on pendrivelinux.com that automatically created the files and configs needed for the USB stick, I also tried the FromUsbKey-FAQ and did it manually. I also tried just Syslinux -S D: ( D: is the USB stick ) but it still won't boot. Just gives the no bootable partition. I tried formatting the usb stick in both FAT and FAT32, neither worked.

---

### Post by LaRoza on 2007-12-25
Your problems could easily be solved if you had a CD drive.

Booting from USB is not a reliable boot method, even in systems that should do it.

Resizing the Windows partition from Windows is not very helpful, as Windows will restrict the size you can shrink to. 

I never did an install the way you are doing, so I can't really help. (Except to advise you to get a optical drive, try the Mad Dog Multimedia drives, they work great)

In Windows, run this command:

```

chkdsk /F c:

```

You will have to let it do it when your reboot. It should fix any errors on the hard disk.

---

