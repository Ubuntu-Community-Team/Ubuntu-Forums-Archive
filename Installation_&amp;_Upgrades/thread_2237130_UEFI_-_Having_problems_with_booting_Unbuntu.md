---
title: "UEFI - Having problems with booting Unbuntu"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by nesh2 on 2014-07-30
Hi I just installed ubuntu today, everything seemed fine but when I try to restart my laptop I only see Windows 8.1 in the boot manager and don't see Ubuntu. I was only able to access Ubuntu by using the installation USB. I tried to do do a boot-repair, but I had an error and this is what I was given [http://paste.ubuntu.com/7909314/](http://paste.ubuntu.com/7909314/) .

---

### Post by oldfred on 2014-07-30
It says grub reinstalled correctly.

 Reinstall the GRUB of sda9 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

But I think Boot-Repair was checking grub file names and with 14.04 the names have changed.

But it looks like you have a Sony. What model?
Sony's only boot Windows. They modified UEFI against UEFI standard to look for Window in UEFI boot description.

There are multiple ways posted as work arounds.  Some work better on some systems but you can try any of them. Also see what other Sony users did. Several uses the one shown as A1 or rename bootx64.efi.

      
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
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[URL="http://www.rodsbooks.com/refind/getting.html"]http://www.rodsbooks.com/refind/getting.html

[/URL]
  HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)
 Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)
UEFI With encryption but you do not have to and with efi file boot rename
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)
One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)
Sony Vaio & Ubuntu 13.10
 [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512)
Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[URL="https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21"]https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21

[/URL]

[URL="http://www.rodsbooks.com/refind/getting.html"]
[/URL]

---

