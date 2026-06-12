---
title: "Ubuntu 14.04 not booting up after install"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by netuser121 on 2014-04-27
Hi,
I've installed ubuntu 14.04 on my pc along with my preinstalled Windows 8.1.
But now when I start my pc, it boots directly to Windows. No grub screen appears and no ubuntu is found in the UEFI boot list.
I tried to repair with boot-repair, but it gave some errors. Check the following link.
[http://paste2.org/GZa4bc5C](http://paste2.org/GZa4bc5C)

Pl help.

- netuser121

---

### Post by oldfred on 2014-04-27
Have you changed UEFI to boot ubuntu entry. Some systems have one boot  selection for hardware devices and a separate one for UEFI boot options.  Others have only one list. And if secure boot is on only the installed  secure boot options will be shown.

You show many boot order lists. Not sure why UEFI systems have lists,  but I assume one is secure boot, one is UEFI and one is BIOS?
BootOrder: 0002,2001,3000,3002,3003,2002,2003
Boot0000* Windows Boot Manager
Boot0001* USB Hard Drive (UEFI) - JetFlashTranscend 4GB
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot0002* ubuntu.

It does look like you installed with the signed versions of grub &  kernels so it should boot with secure boot on. Have you tried with  secure boot off?
What model HP?
       [SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)

---

### Post by netuser121 on 2014-04-28
I dont see ubuntu entry in the UEFI list. I have attached a snap of my UEFI screen. Same options are shown whether secured is on or off.
Secured boot is disabled.
The laptop model is HP G6 2301ax.
Is there any other way set boot priority?

---

### Post by oldfred on 2014-04-28
I do not even see Windows as boot option. Just OS boot manager. What does that do?

Some change files around.
You can rename Windows efi file so system thinks it boots Windows but really boots grub. (Boot-Repairs 'buggy' fix)
You can rename bootx64.efi and when booting hard drive that file is used.
Or you can add entry to BCD.

       Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
The booting device or hard drive works also.


 Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by netuser121 on 2014-04-30
@oldfred
Thanks for your replies..
Successfully booted Ubuntu on my hp laptop.
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it 
1) press esc key while booting to access start up menu
2) press F9 for boot devices menu. 
3) list of boot devices incl. OS boot manager & ubuntu. Select ubuntu.Grub 2 screen will be displayed. Select ubuntu to boot to ubuntu.
However selected boot device is only for the current boot.
You have to do this every time you start.
Also I think you have to follow this for most of the hp laptops with similar firmwares.

---

### Post by oldfred on 2014-04-30
Glad you got it working.

Most with HPs have reported issues and not being able to set Ubuntu as default. 
If you can boot that way it may be better than all the file rename hassles.

Some have reported (not sure if HP) good success with rEFInd. 

 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

