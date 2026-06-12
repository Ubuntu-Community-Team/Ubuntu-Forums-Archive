---
title: "Can't install Windows alongside Ubuntu."
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by KuJiM on 2015-10-07
I have created a NFTS partition using Gparted tool and I have the Windows 7 on a USB stick. 
The problem is that the Windows installation does not come up when I restart the PC (and yes, I have changed the boot order in BIOS).

See screenshots.

What Am I missing here ?


Oliver

---

### Post by yancek on 2015-10-07
How did you get the windows 7 install medium on the usb?  If you have your computer set to boot from the usb first and it doesn't, then something is wrong with the usb.  Booting a windows installer from a usb is possible, even from Grub but if it doesn't work I think you would be better off posting your windows questions on a windows forum.

---

### Post by KuJiM on 2015-10-07
"How did you get the windows 7 install medium on the usb?"

- I used windows 7 usb installer tool in a windows PC to burn the ISO image on the USB.

---

### Post by grahammechanical on 2015-10-07
I have run Windows 8 preview edition from a DVD live session and installed it from the live session into a partition at the start of the hard disk. But I do not think that you can do that with Windows 7. 

> [COLOR=#252525][FONT=sans-serif]Before Windows 8, only embedded versions of Windows, such as [/FONT][/COLOR][Windows Embedded Standard 7]("https://en.wikipedia.org/wiki/Windows_Embedded_Standard_7")[COLOR=#252525][FONT=sans-serif], supported booting from USB storage devices.[/FONT][/COLOR]

[https://en.wikipedia.org/wiki/Windows_To_Go](https://en.wikipedia.org/wiki/Windows_To_Go)

Regards.

---

### Post by oldfred on 2015-10-07
Windows 7 default is a BIOS install. And Windows in BIOS will not install to a gpt partitioned drive.
Windows only boots from gpt with UEFI.
Windows only boots from MBR(msdos) with BIOS.

You can convert your Windows flash drive to a UEFI boot installer with a few minor changes.
        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

[FONT=arial]A) On the **USB flash drive**, "copy" the **efi\microsoft\[COLOR=#ff0000]boot[/COLOR]** folder up one level into the **efi** folder as **efi\[COLOR=#ff0000]boot[/COLOR]**. 
[/FONT]
Windows really prefers you have another small 128MB partition just before the first NTFS partition.
       
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by KuJiM on 2015-10-09
Hey oldfred. 

I have decided to install Windows 10 instead. I have a different error now, it says "Secure Boot Fails" when I try to install Windows.

Do I need to disable secure boot ?

My laptop is an ACER and the BIOS version that I have does not allow me to disable the secure boot. I am not too sure what to do.

---

### Post by KuJiM on 2015-10-09
Manged to install Windows. After disabling secure boot I was able to install Windows 10.

---

### Post by oldfred on 2015-10-09
All systems, so far have a way to disable secure boot. It is a requirement. 
But Windows of all systems should install with secure boot on.

       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

