---
title: "Ubuntu failed to install grub2"
date: 2018-01-19
forum: Installation &amp; Upgrades
---

### Post by barrosinsanus on 2018-01-19
Hi everyone,

When installing Ubuntu or Lubuntu, it always crashes when it tries to install grub2. I've followed the Boot-info tutorial and my URL is: [http://paste.ubuntu.com/26418533/](http://paste.ubuntu.com/26418533/)

Any suggestion?

Thanks  ;)

EDIT: I have a ASUS X550cc and windows 10 installed in another disk partition.

---

### Post by ubfan1 on 2018-01-19
You have a legacy install of Windows 10 on a dos partitioned disk.  Are you sure you are booting the Ubuntu install media in legacy mode?  If you try to install in UEFI mode, grub will fail because it will have no location to install (no EFI partition).

---

### Post by barrosinsanus on 2018-01-19
I'm not sure. How do I see that? In BIOS when restarting the laptop?

Thanks.

EDIT: My BIOS (in BOOT Configuration) only has Launch CSM and Launch PXE OpROM options.

---

### Post by oldfred on 2018-01-19
Did you re-install Windows in BIOS mode?
You system has UEFI and you booted live installer in UEFI mode.
But with Windows in BIOS boot mode on MBR drive, you want to install Ubuntu in BIOS boot mode also.

It also says this:
 "GUID Partition Table detected, but does not seem to be used. "

If drive was gpt(GUID) and you installed Windows in BIOS mode it incorrectly converted drive from gpt to MBR.
You have to remove backup gpt partition table(one of advantages of newer gpt).

      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

Windows in BIOS boot mode must have MBR partitioning. 
Windows in UEFI boot mode must have gpt partitioning.

Be sure to boot Ubuntu live installer in BIOS boot mode, run fixparts then reinstall grub.

You must have CSM on, but separately also have to boot flash drives in BIOS boot mode. UEFI will normally show two boot options for live installer on flash drive.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

