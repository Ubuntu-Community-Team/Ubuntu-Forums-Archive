---
title: "Windows 8 ubuntu dual boot"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by krishnan t s on 2015-02-18
Hi all,
I need an urgent reply on this please!!

I have ubuntu 14.04.1 LTS installed on my laptop with switchable AMD graphics card. I want to install windows 8.1 alongside ubuntu and for that i have decided to erase ubuntu completely, install windows first and then reinstall ubuntu 14.04 and optionally ubuntu desktop next 15.04(if i can finish downloading it on my *SARCASTIC* super fast connection).

 The problem is that ubuntu only installs properly when the bios is set to legacy mode and i install it from the EFI live disk i created(meaning ordinary install fails to work when bios is set to legacy mode and efi install also fails when bios is set to efi mode funnily). I successfully overwrote windows 8.1 over ubuntu but at the time of installing ubuntu, the installer warned me that installing ubuntu in UEFI mode could lead to other operating systems installed in legacy mode not getting detected. 

Is it possible to set the boot to efi mode, install windows and then use the live EFI disk to install ubuntu(changing bios back to legacy mode)? If so,
1. How do i create a bootable windows usb for UEFI in ubuntu?
2. Is there any problem i may face either during or after install? Also, are there any other steps i need to follow to dual              boot?(eg turning off fastboot secureboot etc)
3. If i triple boot ubuntu desktop, desktop next and windows, will grub detect all 3 operating systems?(i will install grub to       mbr)
4. what is the difference between gpt and mbr? which should i use for the purpose of triple boot?

If the above situation is not possible, i'm totally willing to sacrifice windows and retain ubuntu as i have it as my primary system at both office and home. Thanks for patiently reading a long post.

---

### Post by oldfred on 2015-02-18
Only some answers.
Windows only boots in UEFI mode from gpt partitioned drives. Or if drive is gpt then you must install Windows in UEFI mode.
Windows only boots in BIOS from MBR(msdos) partitioned drives.

Installer must be booted in mode UEFI or BIOS that you plan to install.
And all systems must be installed in same boot mode to be in grub menu. And UEFI will probably not have two entries for two ubuntu installs as both will be in same efi folder. But grub menu will have both if both are UEFI.

Some hardware vendors (actually many it seems) modify UEFI to only boot by description in UEFI the Windows entry. That is not per UEFI standard. But there are multiple work arounds, some better than others depending on hardware & configuration.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
GPT or MBR
[URL="http://ubuntuforums.org/showthread.php?t=1625285"]http://ubuntuforums.org/showthread.php?t=1625285

[/URL] Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[URL="http://ubuntuforums.org/showthread.php?t=1625285"]
[/URL] [http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

[ ]("http://ubuntuforums.org/showthread.php?t=1625285")

---

### Post by krishnan t s on 2015-02-21
Hi,
Thanks for the reply. Have successfully managed to triple boot on efi. I still dont know how to create a bootable windows usb in ubuntu. Had to use a program called rufus on my desktop to do it. If anyone has any link to do this(for future reference) on ubuntu, please post it here. Marking this thread as solved :)

---

