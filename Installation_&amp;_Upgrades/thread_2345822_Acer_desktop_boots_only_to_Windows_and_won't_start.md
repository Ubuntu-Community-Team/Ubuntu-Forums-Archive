---
title: "Acer desktop boots only to Windows and won't start Ubuntu"
date: 2016-12-08
forum: Installation &amp; Upgrades
---

### Post by btedm on 2016-12-08
I recently purchased an Acer Aspire TC-270 desktop with bios version R01-A4 and Windows 10 pre-installed.  In Windows 10, I reduced the size of the Windows partition.  I  started the Ubuntu 16.04 installation, made new partitions and installed Ubuntu 16.04 64 bit.  The install completed and I was asked to reboot.  On reboot, the machine went directly to Windows.  I restarted and in the bios I pressed F12 to display the boot menu.  The only option available is the Windows Boot Manager.  I could not run Ubuntu.

After many attempts, I had success with the command from an administrator terminal in Windows:

```
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
```

I can now see the grub2 menu and select either Ubuntu or Windows.  The problem is solved.

Comments and earlier attempts:
After a Windows update, the machine booted directly to Windows again and I had to enter the bcdedit command again.  
The F12 boot menu still displays Windows Boot Manager as the only option.  However now it loads grub2 instead of windows.

I used a version of the fix given in: [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi").  However the command suggested in this link used the executable grubx64.efi instead of shimx64.efi.  I executed the bcdedit command with grubx64.efi and then it was necessary to disable secure boot.  Later I executed the bcdedit command with shimx64.efi and re-enabled secure boot.  Thanks to the help from people at Launchpad who responded to bug 1641793 and explained what to do.

I had previously tried Boot-Repair when the machine was booting only windows, but it did not help.  It  wrote some backup files into the /boot/EFI folder which I later deleted.

Although it did not solve my problem, the site [http://www.rodsbooks.com/efi-bootloaders/]("http://www.rodsbooks.com/efi-bootloaders/")  gave a lot of useful information.  The site explained how to look at the folders in /boot/EFI.   I thought it was safer to look at the files in the folder to ensure that there really was a shimx64.efi before I set the bcdedit command to use it.  However, I tried the command efibootmgr discussed therein, and found that I had a loader for Ubuntu but it was not enabled (Boot0000  ubuntu).  I enabled it, checked that it was enabled, but the next time I booted it was disabled again.  After the windows bcedit command I can start Ubuntu, although the efibootmgr still shows the loader for Ubuntu as disabled.  So efibootmgr did not help.

---

### Post by oldfred on 2016-12-08
Every Acer we have seen,need you to set a UEFI supervisory password, and then in UEFI drill down in ESP - efi system partition and enable "trust" on the grub/ubuntu boot files.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

