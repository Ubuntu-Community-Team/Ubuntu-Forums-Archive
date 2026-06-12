---
title: "dualboot windows 8.1 and 13.10"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by rbduck13 on 2013-11-17
Hi all

I trying to dual boot ubuntu and windows. I have it installed I'm just very confused as to how to get Windows to control the boot loader instead of grub. When I turn my laptop on it goes straight into grub but I want it to do this [IMG]http://img0.tuicool.com/aMnYR3.png[/IMG] I did a boot-repair but i really dont know if I just made it worse [http://paste.ubuntu.com/6430705](http://paste.ubuntu.com/6430705). If you help it would be greatly apprieciated sorry if this has already been asked if thats the case can you just direct me in the right direction

---

### Post by fantab on 2013-11-17
I don't think you can use Windows boot loader to boot Linux/ubuntu. You can try [EasyBCD]("http://neosmart.net/EasyBCD/"), but I don't really know how it works, I have never used it. EasyBCD can be troblesome with UEFI booting.

Seriously, what difference does it make who controls your boot as long as you can boot both? Can you boot both, Windows and Ubuntu from Grub. Moreover when you boot you only see grub for 10secs more or less.

Do you want Windows to be your Default boot? Do you want your computer to boot straight to Windows and Not Ubuntu?
This can be easily done.

---

### Post by oldfred on 2013-11-17
With UEFI you do not need EasyBCD. With BIOS boot you can only install one boot loader and that controls booting. Some preferred Windows and used EasyBCD, so grub was not in MBR.

But with UEFI all boot loaders exist side by side in efi partition. You set which is default in UEFI, just like you do in setting DVD or flash drive or which hard drive is first in boot order. With UEFI you set which device or entry in efi partition to boot first.

       It looks like Boot-Repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.

   [COLOR=#b22222]
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.[/COLOR]

    If you cannot boot ubuntu from UEFI menu running the un-rename may prevent you from booting Ubuntu.

From your report line 535
      >  BootOrder: 0003,[COLOR=#ff0000]0000[/COLOR],0001,2003,2001,2002
Boot[COLOR=#ff0000]0000[/COLOR]* Windows Boot Manager    HD(2,200800,82000,ebf27fb2-33f0-11e3-9163-aa4b2309c98c)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................
Boot0001* Ubuntu    HD(2,200800,82000,ebf27fb2-33f0-11e3-9163-aa4b2309c98c)File(EFIubuntugrubx64.efi)RC
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-69-0B-A6)     ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(008cfa690ba6,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0003* ubuntu    HD(2,200800,82000,ebf27fb2-33f0-11e3-9163-aa4b2309c98c)File(EFIubuntushimx64.efi)
Boot0004* EFI Network 0 for IPv4 (00-8C-FA-69-0B-A6)     ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(008cfa690ba6,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0006* EFI DVD/CDROM    RC
Boot0007* EFI Network    RC
etc



You are showing 0003 as default or ubuntu in your UEFI menu. Change to Windows and it should be 0000

You can also change those entries with efibootmgr from command line.

This was how to set grub as default from Windows, you you can change to set Windows as default.
 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

---

