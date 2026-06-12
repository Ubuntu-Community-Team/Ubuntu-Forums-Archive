---
title: "Switch Boot-Loader"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by user0182 on 2007-10-05
Hi All,

I have a laptop, on which I have partitioned the hard disk into 5 partitions. One for MS Windows Vista, one for Vista recovery, one for Ubuntu, one for Ubuntu virtual memory swap space, and one FAT 32 formatted partition to share files.

My question is, could someone tell me how to change my boot loader from GRUB to the Windows Vista boot loader?


Thanks in Advance

---

### Post by eluzi on 2007-10-05
I found this at Google...not sure wheter it helps u cos' i guess u've already got it installed right ?

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx")

---

### Post by user0182 on 2007-10-06
Ye, I have already installed it :-(. I need to change from the GRUB boot-loader to the Windows one :-|.

Thanx Anyway,

---

### Post by confused57 on 2007-10-06
If you have a Vista install dvd(not a recovery disk), you could use the bootrec.exe utility to restore your Vista bootloader:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

If you don't have a Vista install dvd, you can use this utility:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)
[http://ubuntuforums.org/showpost.php?p=2809942&postcount=22](http://ubuntuforums.org/showpost.php?p=2809942&postcount=22)

Once you've restored Vista's IPL to the mbr, you can use EasyBCD to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

You'll need to install grub's IPL to the root partition, using the Ubuntu live cd, in order to boot Ubuntu with Vista's bootloader:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Using these instructions, you would do something like "setup (hd0,2)" instead of "setup (hd0)".

---

