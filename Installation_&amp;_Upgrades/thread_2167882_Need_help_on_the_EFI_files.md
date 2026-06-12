---
title: "Need help on the EFI files"
date: 2013-08-15
forum: Installation &amp; Upgrades
---

### Post by Lim_Xiang_Yann on 2013-08-15
I used [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)
and accidentally used "restore mbr" on my ASUS A55V lappy that is EFI in it.
then i stirred the things up, and now, i succeeded on booting my kali linux and ubuntu but not the windows 7 64 bit

I'm totally new to this territory, so I need help~~
now my boot file points to /boot/efi
and the recovery partition is accessible on linux-based os.

This is my current 25_custom file in /etc/grub.d

```
#!/bin/sh
exec tail -n +3 $0

menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root F077-A6AD
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root F077-A6AD
chainloader /EFI/Boot/bootx64.efi
}
```

Now Windows 7 boot with error 0xc000000f
that the required device is inaccessible

Repair Disc tried, but says not for my laptop
Windows 7 Disc - repair tried, same as above

---

### Post by ubfan1 on 2013-08-15
Maybe try adding the root to the path in grub.cfg (and in the custom file like:
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi

---

### Post by oldfred on 2013-08-15
Post the link to the BootInfo report that Boot-Repair creates,
But it sounds like it just is a Windows error and you need to use you Windows repair flash drive to fix it. Windows 7 is usually BIOS with MBR partitioning, so I am not sure if you need a different repair flash more like the Windows 8 version.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 [http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by Lim_Xiang_Yann on 2013-08-17
Thanks for helping!
Trying now and will give an update after it's done.

---

### Post by Lim_Xiang_Yann on 2013-08-18
now I got another problem...
that is, it can't seem to find an operating system from my hard drive but it exists

---

### Post by oldfred on 2013-08-18
If UEFI/BIOS you have different ways to boot from UEFI. You have UEFI which then has to find boot files in the efi partition. And you have Compatibility Support Module (CSM), which emulates a BIOS mode and will boot from the MBR.

Post the link to BootInfo report. Part of Boot-Repair.
       [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Lim_Xiang_Yann on 2013-08-19
Thanks for replying, but I'm already dumped my laptop to the manufacturer's place XD
Thanks again for getting a reply that fast.

---

