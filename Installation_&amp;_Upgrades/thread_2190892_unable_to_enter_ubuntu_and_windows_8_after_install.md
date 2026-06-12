---
title: "unable to enter ubuntu and windows 8 after installation of Ubuntu 12.04 LTS"
date: 2013-11-29
forum: Installation &amp; Upgrades
---

### Post by jjling on 2013-11-29
Hi,

I have a dell desktop machine with win 8 pre-installed.  I used Ubuntu for quite a while, so I decide to make a dual-boot system. After install the Ubuntu 12.04, however it is unable to enter either of the system.   I have spent quite a lot of time and looked up for the solution online, generally I followed the Boot-Repair default method, however no good luck. I am wondering if it modified my the MBR and unable to load either file.  I am posting my boot-repair log in the web, [http://paste.ubuntu.com/6497048/](http://paste.ubuntu.com/6497048/)  Can the expert kindly have a look and help me?

Thanks,

JJ

---

### Post by ubfan1 on 2013-11-29
Looks like you have the proper setup for a secure boot enabled Ubuntu.  Can you select the efi boot loader (some function key, varies by machine) and select ubuntu, and have it run?  If that works, just change the boot order with efibootmgr, to boot that entry first instead of the flash drive(?).

---

### Post by jjling on 2013-11-29
Hi,

Thank you for your replying.  Can you explain it more?  Where can I find the efi boot loader?  Do you mean the boot sequence in the BIOS?

JJ

---

### Post by oldfred on 2013-11-30
It is not really BIOS anymore but UEFI. 

       It looks like boot repair ran its "buggy" UEFI rename function. 
I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

    
If you can boot the ubuntu entry from UEFI menu, you do not need the rename. If only the Windows entry works which now really boots to grub menu and you can only boot Windows backup file from grub menu with new entry from Boot-Repair.

Boot-Repair extracted this from your UEFI and it shows ubuntu as first entry:
 BootOrder: [COLOR=#ff0000]0002[/COLOR],0003,0000,0001
Boot0000  P0: WDC WD10EZEX-75ZF5A0      	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001  P4: TSSTcorp DVD+/-RW SH-216CB	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot[COLOR=#ff0000]0002[/COLOR]* ubuntu	HD(1,800,fa000,f50dd835-b59f-4263-977f-098cc183b0a4)File(EFIubuntushimx64.efi)
Boot0003* UEFI: Generic Flash Disk 8.07	ACPI(a0341d0,0)PCI(1a,0)USB(1,0)USB(2,0)HD(1,2f0,780510,8bbfcf58)AMBO

---

