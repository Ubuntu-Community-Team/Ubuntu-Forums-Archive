---
title: "Problems with boot-repair"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by williams.roger on 2014-02-04
[TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][CENTER][COLOR=#777777]0[/COLOR]down vote[favorite]("http://askubuntu.com/questions/416499/problems-after-using-boot-repair#")[COLOR=#808185][/COLOR]
[/CENTER]
[/TD]
[TD="class: postcell, bgcolor: transparent"]Installed 13.10 on existing Windows computer. Ran boot-repair, twice actually after the first time didn't work. Ubuntu boots, windows shows up in GRUB but doesn't boot.
Here is the boot-repair report
[http://paste.ubuntu.com/6875256/plain/](http://paste.ubuntu.com/6875256/plain/)
Thanks for input, I'm overwhelmed by things I googled, it seems quite some answers are outdated, not sure about UEFI.


[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2014-02-07
Because you ran the rename & backup function in Boot-Repair this is the only entry that should work.
       "Windows UEFI bkpbootmgfw.efi"

The backup & rename is for those UEFI that are modified by the vendor to only boot Windows. So Boot-Repair has to rename the Windows file, and copy shim/grub to be Windows file.
Generally better not to rename unless you have to.
If you can boot ubuntu entry from UEFI menu undo rename and then you will also be able to boot Windows entry from UEFI menu. With rename both ubuntu entry & Windows entry boot to grub.

      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

It does look like you originally installed Ubuntu in BIOS boot mode. Both Windows & Ubuntu need to be in the same boot mode either BIOS or UEFI. But since Windows is UEFI, Ubuntu needs to be UEFI. 
How you boot install media is how it installs.
      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

