---
title: "Unistall a disfunctional grub on a dual boot system"
date: 2018-08-10
forum: Installation &amp; Upgrades
---

### Post by inferno27 on 2018-08-10
Hi,

I have an Acer Pedator G9-593, with a ssd and a hdd. I attempted to dual boot it with Ubuntu 16.04 alongside Windows 10, but after installing through live usb stick, the grub did not show up during the boot process. 

During the installation of Ubuntu I used the option of "Install alongside Windows boot manager". As far as I understood Ubuntu was installed in the second drive(hdd), while Windows 10 sits in first drive(ssd). But the grub does not show up and my system always boots into Windows 10 irrespective of the boot order in the BIOS and the fact that I disabled secure and fast boot.

 As of now I would like to get my system back to original state with only Windows 10 and without any Ubuntu stuff including the dysfunctional grub, the files for which might have installed somewhere. Please guide me through it as I am a novice in these matters.

Also, after reading some threads I found the summary of my system might help fellow community members in diagnosing the issue better. So below you can find the link to my systems summary report:
[http://paste.ubuntu.com/p/4Qc45vf9h6/](http://paste.ubuntu.com/p/4Qc45vf9h6/)

Thanks a ton in advance.

---

### Post by oldfred on 2018-08-10
It looks like you have a standard Ubuntu install.
But Acer has a unique requirement of setting  an UEFI password and enabling "trust" on the .efi boot files in the ESP.

Many Acer also have needed updates to the newest UEFI from Acer. You  should do that anyway for 
 mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. Both Windows & Ubuntu have updated kernel, support software & downloaded firmware. But UEFI also should be updated.


Several users have described process in more detail, essentially the same.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
    
To totally uninstall Ubuntu you need to remove entries in UEFI boot menu, /EFI/ubuntu folder in ESP and the Linux partitions. You must be sure that Windows is default boot before deleting anything.
       UEFI How To Remove Ubuntu From A Computer Dual Booting With Windows 10 (UEFI only)
How To Remove Ubuntu From A Computer Dual Booting With Windows 10
[http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html](http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html)
Delete /EFI/ubuntu folder from Windows
[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720](http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720)

---

### Post by inferno27 on 2018-08-11
Thanks for the quick reply. 

As mentioned by you I tired to fix the issue with the grub, and now I can boot Ubuntu as well. I followed the steps mentioned in the following link:
[https://ubuntuforums.org/showthread....2#post13369742]("https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742")

Later I did not uninstall the grub  as it works fine now.

---

