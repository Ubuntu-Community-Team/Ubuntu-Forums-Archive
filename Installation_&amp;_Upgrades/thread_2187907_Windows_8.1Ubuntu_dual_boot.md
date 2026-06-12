---
title: "Windows 8.1/Ubuntu dual boot"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by stefano3 on 2013-11-14
Two days ago I installed on my notebook Windows 8.1 and Ubuntu in dual boot. This is how i partitioned my HD:

[IMG]http://i.imgur.com/EpjSkw4.jpg[/IMG]

Now from grub, booting Ubuntu gives no problems. But when I select "Windows Boot Manager" from here

[IMG]http://i.imgur.com/XZjPMLz.jpg[/IMG]

there's an error:

[IMG]http://i.imgur.com/KEfObaW.jpg[/IMG]

Instead, selecting SYSTEM SETUP, and then Windows Boot Manager (see image below), Windows normally starts.

[IMG]http://i.imgur.com/qVYnKuk.jpg[/IMG]

Now my question is: I have done some mistakes during installation? (I don't think, I installed Ubuntu and Windows carefully and manually partitioned HD).
It's a serious problem?
Thank you for your support.

---

### Post by oldfred on 2013-11-14
Generally the efi partition should be near beginning of drive, but I guess now it is not required to be first as I have posted many times. 

Windows has very specific requirements for its partitions including order. Often easiest to just let it install first.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

### Post by ubfan1 on 2013-11-14
This is bug 1091464.  Please add yourself to the "Does this affect me?" list. I have heard claims that is it possible to boot in this situation with secure boot disabled, but cannot verify that.  I have this problem, and use the efi boot menu to select the non-default OS (with secure boot on).

---

### Post by stefano3 on 2013-11-14
First of all thank you both.
I used the "Boot-repair" tool ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and now (after having disabled secure boot) both OSs are bootable smoothly from GRUB.
Actually GRUB list grew, as you can see:

[IMG]http://i.imgur.com/lDAaWnI.jpg[/IMG]

Now, can you explain in short what's the meaning of each line?

And... I read some stuff around but still don't understand the exact meaning of UEFI. It's something like a BIOS? Or more like GRUB?

---

### Post by oldfred on 2013-11-14
UEFI is the new BIOS, but has an mode to work like BIOS for those who have to have compatiblity.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Apple converted to UEFI when it changed to Intel chips, but still has an older version.


 ExtremeTech article on what UEFI is,  from 2011 
[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)

It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.
      
 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

Also grub2's os-prober did not used to find UEFI boot, but only BIOS boot entries. Those would not work with UEFI, so Boot-Repair added correct entries. Only the very newest version of grub creates correctly UEFI boot entry to boot Windows (but it may be shim after rename).

---

### Post by stefano3 on 2013-11-16
Mmm well, but beyond these naming issues, now it's all ok on my notebook? These are only issues regardin booting right? Or I could have problems with OSs executions?

---

### Post by oldfred on 2013-11-16
Some advantage to un-renaming as then you should be able to directly boot either system from UEFI.

Also some Windows updates may reset Windows as default boot, so you may need to change that back. Windows updates may overwrite the shim version and then you can only boot Windows. Bit more maintenance probably required, but systems both should work.

---

