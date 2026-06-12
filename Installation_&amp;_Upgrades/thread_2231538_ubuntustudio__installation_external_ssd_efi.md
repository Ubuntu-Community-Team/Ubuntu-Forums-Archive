---
title: "ubuntustudio  installation external ssd efi"
date: 2014-06-26
forum: Installation &amp; Upgrades
---

### Post by redlab2 on 2014-06-26
Hi all,
Strange things happen to me.
I have win8 on my internal hdd.I have an installation of ubuntu studio 13.10 on an external hdd usb3 along with several other distros.
Recently, I acquired an external ssd drive (Emtec) and tried to install the same ubuntu on it. Before that, I installed on it Linux Mint without problem.
I was not very aware of these EFI things, all I did is disable secure boot and so.
But then, with ubuntu studio, strange things started. After installation, the grub visible was Mint's one.
I switched to Windows 8, so reactivated EFI and then after reswitch to Ubuntu I couldn't boot ; I lost too the grub installed by Mint.
I got a message something like 'no operating system found' when I boot with / without EFI.
I found it funny that in my bios efi menu, I found an ubuntu studio entry after installation but after the switch to Win8 it dissappeared.
I played around to find the trick and discoved that:
- I had ubuntu and ubuntu studio entries in my partition EFI.
- In fstab I have an indication of EFI on my installation of ubuntu studio on my new ssd, but not on my old and good external drive installation.
- It seems that ubuntu studio should have installed in a non EFI mode considering the fact that I booted the live dvd in an unsecure boot.
- same installation process does not yield same result !

Is there a way to force non efi mode at installation time with ubuntu studio 13.10 ?
Any idea of what happened ? Ah, I almost forgot, when I reswitched to win 8, my external ssd was plugged, and I got a message of repairing from windows.
As soon as I saw that, I unplugged the disk.
Bye.

---

