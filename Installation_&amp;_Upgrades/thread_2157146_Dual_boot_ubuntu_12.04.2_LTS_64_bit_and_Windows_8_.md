---
title: "Dual boot ubuntu 12.04.2 LTS 64 bit and Windows 8 on ASUS k55A laptop"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by N2LX on 2013-06-24
Hello,

After many changes to the boot config on windows 8, that include:

1. Disable secure boot (UFEI)
2. Disable fast start
3. Enable CSM so that I can install Ubuntu via DVD

Finally, the installation seemed to complete. But after reboot, I could not boot to Ubuntu. Depending on the boot order, first with Hard disk as the option, for windows I got the PXE error to the effect --  there is no media and to insert some media and retry. Then using DVD as the boot option, I could boot to Ubuntu and as per the suggestion, in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), I tried to grub repair which seemed to fix the boot choices. I now have grub 1.99 with Ubuntu and windows listed as options (along with recovery, Windows-UFEI etc.). I see that, Ubuntu is booted as /dev/sr0. But, If I remove the Ubuntu DVD then then rebooting and choosing Ubuntu takes me to a blank light purple screen (default Ubuntu background) and nothing happens. It appears that I can't access the Ubuntu instantiation on the Hard disk. 

The link for the grub repair is: [http://paste.ubuntu.com/5794468/](http://paste.ubuntu.com/5794468/)

My apologies if the above description is missing details. 

I am looking to get Ubuntu boot off of the hard disk. Any help is greatly appreciated.

Many thanks.

---

### Post by oldfred on 2013-06-24
To easily dual boot both Ubuntu & Windows have to be installed in the same boot mode or both with UEFI. 
When you installed Ubuntu with CSM/BIOS you installed in a different mode. You should then be only able to dual boot by going into UEFI/BIOS turn on CSM & boot Ubuntu, or go into UEFI/BIOS and turn on secure boot and boot Windows.

Some systems only boot Windows with secure boot on, some boot with it on or off(which is how it should be). Also some that boot with secure boot on only will boot the Windows efi file. UEFI is hard coded to look only for that one file to boot to prevent any other system from booting. That is against the UEFI standard.
But Ubuntu has the Microsoft key in grub2's shim file. Boot-Repair can rename the shim file to have the Microsoft efi file name, & backup Windows efi file. Then when UEFI boots shim file (thinking its Windows) and you get grub menu which can chain load back to the renamed Windows efi file to boot Windows. A long way around something that should be relatively simple but made difficult by some system configurations.

Boot-Repair has converted your CSM install to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI). It has also renamed your boot files. But you have not installed the secure boot grub shim file nor the signed Linux kernels to boot Ubuntu in secure boot mode.

Did you boot Windows with secure boot off? Or is your system one that only boots with it on?

If it only boots with secure boot on, you need the signed kernel.
 Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.


This has been done on your system.
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. If yoiur system will boot with secure boot off you can undo the file rename:
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 




 As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 
One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

---

