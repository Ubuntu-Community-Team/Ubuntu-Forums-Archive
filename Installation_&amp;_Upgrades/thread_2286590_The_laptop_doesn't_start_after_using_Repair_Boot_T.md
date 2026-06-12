---
title: "The laptop doesn't start after using Repair Boot Tool"
date: 2015-07-13
forum: Installation &amp; Upgrades
---

### Post by antonio48 on 2015-07-13
Hello,

I bought a Laptop ACER Aspire  V5-573PG with Windows 8.1 in October 2014. Three Months ago i made a  Dual Boot with Kubuntu 14 and I could start Kubuntu pressing F12 and  choosing Kubuntu. Otherwise the laptop startetd always Windows 8.

Last Friday I tried to start in Kubuntu but I couldn't see kubuntu anymore.

Then  I read a little bit and made a Ubuntu Live USB Stick 14.04. Then I  started in Try Ubuntu Mode and installed the Boot Repair Tool. Today I  run this tool with the option Backup and rename Windows EFI files  option.

Everything seemed to work OK and I received this message:

***Boot successfully repaired.***

***Please write on paper the following URL***
***[http://paste.ubuntu.com/11871283/](http://paste.ubuntu.com/11871283/)***

***In case you still experience boot problem indicate this URL to***
***boot.repair@gmail.com or to your favorite support***

***You can now reboot your computer***

***You may want to retry after deactivating the [Backup and rename Windows EFI files] option***

Then i rebooted the PC and I received these Messages:

**HDD0: has been blocked by the current security policy.**

Then I press OK and can see:


**Default Boot Device Missing or Boot Failed.**
**Insert Recovery Media and Hit any Key.**
**Then select Boot Manager to choose a new Boot Device or to Boot Recovery Media.**


Please help me.
Thank you very much.

Antonio

---

### Post by oldfred on 2015-07-13
I thought the new versions of Boot-Repair did not rename the Windows efi boot file /EFI/Microsoft/Boot/bootmgfw.efi. While that works and Windows update then undoes the change and grub stops working. And you only can boot Windows from grub not UEFI.

Now preferred choice is to copy grub and/or shim to /EFI/Boot and rename to bootx64.efi. Then you can boot hard drive entry in UEFI and still boot Windows directly from UEFI.

Do you still have secure boot on in UEFI? Boot-Repair says it is on.

Did you leave fast startup on in Windows. Grub will not boot Windows with secure boot on or if Windows has its fast startup on which really is just always on hibernation. Boot-Repair says it is in unsafe state which is either fast startup or it needs chkdsk. Or both. It needs chkdsk after any resize also.

 Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]http://www.youtube.com/watch?v=QGiG1oljjZI
[/URL]
 Screen shots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)


Acer also seems to require you to set a UEFI password (never lose that) and then you can set trust on ubuntu entry in UEFI and boot it.

        Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

            Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

            How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

    
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by antonio48 on 2015-07-13
Thank you very much for your answers. I tried to start with Legacy and then the system said:
PXE-M8F: Existing PXE ROM
No bootable device. Insert boot disk and press any key.

Then i tried to put UEFI and Secure Boot Disabled and then i could see a grub Menu with black screen with 6 or 7 Options. Then i tried to take a foto and the system started automaticallly in Windows again.

After this i tried to enable and disabled the Secure Boot again trying to get this menú again but i can't get it anymore...

I am in the same status as i was before running the Boot Repair Tool. Also i can see only Windows in the Boot Menu.

---

### Post by oldfred on 2015-07-13
You want secure boot off, but UEFI on. The legacy/CSM/BIOS should then also be off.

Did you set a password? That opens more options to allow you to set.

Your Info did not yet show an Ubuntu entry in your UEFI boot options. You need to run Boot-Repair again. Undo any rename. and run a full reinstall of grub. That is in advanced options not any auto fix.

---

### Post by antonio48 on 2015-07-16
Finally i set a password and set secure boot off but UEFI on.  Then the laptop started in Windows. Then i could shut off the laptop. Then with the USB Live Ubuntu i run Boot Repair again in advanced options as you told me. The I rebooted again and I could with the F12 see both possibilities: Windows Boot and HDD0. Before i could read Windows Boot and Ubuntu. But when i press on HDD0 then i see a grub menu and there i can choose ubuntu and many other options. For me is ok so. Also thank you very much for your support!. We can set this message now as SOLVED.

---

