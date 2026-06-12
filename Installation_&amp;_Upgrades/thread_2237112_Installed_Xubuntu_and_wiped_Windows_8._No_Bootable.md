---
title: "Installed Xubuntu and wiped Windows 8. No Bootable Device found upon restart"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by Pee_Dubbayu on 2014-07-30
Have a new Toshiba Satellite C55D-B5212 Laptop with AMD A8 CPU.
Wiped Windows 8 during installation of Xubuntu.
When Live CD says restart computer after installation after ejecting Live disc,
the Toshiba screen pops up then says [B]No bootable device -- insert boot disk and press any key
[/B]I was able to run Boot-Repair recommended repair from Live but it did not do the trick.

Here is the Boot Info Script from Boot-Repair: [http://paste.ubuntu.com/7893074](http://paste.ubuntu.com/7893074)

Thank you for any help. I have researched this forum and others extensively to no avail.

---

### Post by oldfred on 2014-07-30
It says grub reinstalled correctly.

       Reinstall the GRUB of sda2 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

You show signed kernels installed so it should boot with secure boot on. Have you tried with secure boot off, but UEFI on in UEFI/BIOS?

I thought Toshiba's worked, but Sony & HP only boot Windows so we have work arounds to change Windows efi file or name to really be grub or shim (grub for secure boot). Then UEFI thinks it boots Windows, but actually boots grub.

Another user with similar model:
      [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
 [http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

 Post this:
sudo efibootmgr -v
The version in BootInfo report shows entries but not detail. Link above shows all the detail with two ubuntu entries, one actually grub and the other shim.

---

### Post by Pee_Dubbayu on 2014-07-31
I tried with Secure Boot disabled with UEFI on and it did not work. I also tried CSM boot and it didn't work either.



[FONT=arial]ubuntu@xubuntu:~$ sudo efibootmgr -v[/FONT]
[FONT=arial]BootCurrent: 0003[/FONT]
[FONT=arial]Timeout: 0 seconds[/FONT]
[FONT=arial]BootOrder: 0004,0005,0006[/FONT]
[FONT=arial]Boot0000* ubuntu    Vendor(99e275e7-75a0-4b37-[/FONT][FONT=arial]a2e6-c5385e6c00cb,)[/FONT]
[FONT=arial]Boot0001* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,[/FONT][FONT=arial]0)MAC(f8a963cb0ab4,0)IPv4([/FONT][0.0.0.0:0]("http://0.0.0.0:0/")[FONT=arial]<->[/FONT][0.0.0.0:0]("http://0.0.0.0:0/")[FONT=arial],0, 0..BO[/FONT]
[FONT=arial]Boot0002* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,[/FONT][FONT=arial]0)MAC(f8a963cb0ab4,0)[/FONT][FONT=arial]030d3c000000000000000000000000[/FONT][FONT=arial]000000000000000000000000000000[/FONT][FONT=arial]000000000000000000000000004000[/FONT][FONT=arial]000000000000000000000000000000[/FONT][FONT=arial]..BO[/FONT]
[FONT=arial]Boot0003* UEFI: HP v125w 4096    ACPI(a0341d0,0)PCI(12,0)USB(1,[/FONT][FONT=arial]0)USB(1,0)HD(1,30,777fd0,[/FONT][FONT=arial]c3072e18)..BO[/FONT]
[FONT=arial]Boot0004* UEFI:CD/DVD Drive    BIOS(81,0,00)[/FONT]
[FONT=arial]Boot0005* UEFI:USB Device    BIOS(82,0,00)[/FONT]
[FONT=arial]Boot0006* UEFI:Network Device    BIOS(83,0,00)[/FONT]

---

### Post by oldfred on 2014-07-31
I do not know if something changed, but your ubuntu entry with Vendor does not look correct.

Most look like the one the user in the link to a similar system above has, which shows booting with grub:

 Boot0000* Ubuntu    HD(2,200800,32000,dfcdafe9-6cd2-11e3-989e-cc2ea1910b0e)File(EFIubuntu[COLOR=#ff0000]grubx64[/COLOR].efi)RC

Do you also have a grub.cfg in you /efi/ubuntu folder? It should have an entry that is configfile pointing to use the real grub.cfg in your install.

I might reinstall grub with secure boot off.

On the systems that only boot Windows this is a list of the work arounds. Some seem to work better than others, but several have suggested a1 the rename of bootx64.efi. If you do not have that directory, you can just manually create it.


 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
**a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
**a2:**(this is the same as what Boot-Repair does in B:. 
Rename /efi/Microsoft/Boot/bootmgfw.efi and copy grub or shim into /efi/Microsoft/Boot and name it bootmfgw.efi  Then boot Windows entry to boot to grub menu. You have to manually add a grub menu entry to boot renamed Windows efi file. Grub2's os-prober entry boots bootmfgw.efi entry which is now just grub, so it will not work.

   Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)


      
 From a working computer otherwise mount partition and include mount in every command:
cd /boot/efi/EFI
sudo mkdir -p BOOT
sudo cp ubuntu/shimx64.efi BOOT/bootx64.efi
sudo cp ubuntu/grubx64.efi BOOT/grubx64.efi

---

