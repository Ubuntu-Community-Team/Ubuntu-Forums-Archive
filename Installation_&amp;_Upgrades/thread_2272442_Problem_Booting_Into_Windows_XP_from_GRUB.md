---
title: "Problem Booting Into Windows XP from GRUB"
date: 2015-04-06
forum: Installation &amp; Upgrades
---

### Post by cobalt2 on 2015-04-06
Ever since I installed Ubuntu UU on my system, it has hijacked my system so that I'm no longer able to boot into Windows. 
](*,)

Whatever I attempted in fixing the problem was unsuccessful. I used Boot Repair, and chkdsk /r. I looked for the file root.disk in [COLOR=#333333][FONT=Ubuntu Beta]ubuntu\disks and couldn't find it. Couldn't find those hidden directories [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]C:\found.000 or dir0000.chk either. 

Here is the URL from the pastebin:
[/FONT][/COLOR]http://paste.ubuntu.com/10754235/

I'm running Ubuntu UU 14.10 64 bit, and Windows XP Home Edition 32 bit. I have XP on the 1st partition and UU on the 2nd.

Anyone have any ideas how to fix the problem?

---

### Post by oldos2er on 2015-04-06
Wubi is no longer supported even though it still exists in the 14.10 image file. 

Have you tried what bootinfo suggested? "A broken Wubi has been detected. Please fix it this way:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu) "

---

### Post by Mark Phelps on 2015-04-06
>  I have XP on the 1st partition and UU on the 2nd.If that is the case, then why are there references to wubildr in the report?

Did you try to install using Wubi, have that fail, and then resorted to a different install with Ubuntu having its own partitions?

---

### Post by cobalt2 on 2015-04-06
[QUOTE=]If that is the case, then why are there references to wubildr in the report?[/QUOTE]
What is wubildr?

[QUOTE=]Did you try to install using Wubi, have that fail, and then resorted to a different install with Ubuntu having its own partitions?[/QUOTE]
I successfuly used the wubi to install Ubuntu on my system.

---

### Post by oldfred on 2015-04-07
Your summary report showed this with several wubi boot files, but not root.disk:

```
sda1: ______________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr
```

And then you also show a full install in sda5.

Grub really only boots a working Windows, so you need to repair Windows with your XP install disk and its repair console.

---

### Post by cobalt2 on 2015-04-07
> **oldos2er said:**
> Wubi is no longer supported even though it still exists in the 14.10 image file. 

Have you tried what bootinfo suggested? "A broken Wubi has been detected. Please fix it this way:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu) "

I tried the recommendation in the wiki for repairing my Windows XP installation, and it was unsuccessful. I ran the Windows Recovery Tool, and used the chkdsk /r command to check the disk for errors and repair them.

---

### Post by cobalt2 on 2015-04-07
In Windows Recovery Tool, I used fixmbr to replace GRUB with Windows Boot Loader, since I thought that GRUB could  be incompatible with my XP installation. Then I booted my system, instead of getting an OS menu, I received a disk not readable error. At that point I realized the Windows NTFS must be damaged, so formated the partition and reinstalled it. After reinstalling Windows, I lost the GRUB. I installed wubi with the option of adding Ubuntu to the Windows Boot Loader, thinking that I could boot my Ubuntu installation from there. Instead it booted into the wubi Ubuntu. 
    
In Windows I have a problem which is absolutely mystifying. The standby option is missing! At the time when I reinstalled, I had BIOS option for turning off hard disks set to 10 minutes. So I disabled this setting, thinking that it was interfering and incompatible with Windows. The standby option is still missing. Is it possible that this BIOS option permanently disabled standby?

---

### Post by oldfred on 2015-04-07
Do not know about standby in Windows.
But do not use hibernation if dual booting.

But if you now have Windows working, you should just reinstall grub2 as boot loader. 
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by cobalt2 on 2015-04-13
I was able to solve the missing standby button problem by installing the driver for my graphics card. I installed the GRUB, and now I'm finally able to use the GRUB to boot Windows XP.

---

