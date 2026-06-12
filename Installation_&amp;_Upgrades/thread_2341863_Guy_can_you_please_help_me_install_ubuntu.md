---
title: "Guy can you please help me install ubuntu"
date: 2016-11-01
forum: Installation &amp; Upgrades
---

### Post by lown on 2016-11-01
Hey guys,
I have an Acer Laptop with the following specification: 
CPU: Intel Core i7-6500 2.5GHz with  Turbo Boost up to 3.1GHz
Graphics Card: NVIDIA GeForce 940M with 2GB Dedicated VRAM
RAM: 8GB DDR3 L Memory
HDD: 100GB (1 TB)
---------------------------------------------------------------------------------
I need to install Ubuntu on my laptop but at the same time keeping Windows 10. I have a UEFI bios. I tried many YouTube videos but none of them worked. What happens is that when I installed Ubuntu, the dual boot menu doesn't show. Windows 10 would just load automatically. Can you please help me in regards to how to solve this problem? And what things I should have my laptop at to be able to dual boot. 
Ubuntu is very important for my studies.  
Thank you!

---

### Post by ajgreeny on 2016-11-01
This paragraph from the thread at [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) may be part of your problem so have a good read through that and see if it helps in any way.
> **Systems that only boot Windows from UEFI.**

Per UEFI standard you should be able to boot any entry in UEFI boot menu. But some vendors have modified UEFI code to only boot the Windows efi file. The UEFI looks for the Windows file name and only boots it. (Note for Acer, it requires "trust" settings in UEFI)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI with the 64bit version with secure boot on. A few systems will only boot with UEFI and secure boot on or with CSM (BIOS) if secure boot is off. Best to test system to see which modes it boots in. In secure boot mode it will only show/allow systems that have secure boot. You may have to change UEFI settings or set password to allow other devices to boot.

---

### Post by oldfred on 2016-11-01
Acer is unique in that you have to set a UEFI password and enable trust from UEFI on the ubuntu/grub .efi files in the ESP.
Also some older threads mention downgrading UEFI, but newer ones mention newest UEFI from Acer works, so make sure you have newest UEFI from Acer for your system.

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
      
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    [URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

