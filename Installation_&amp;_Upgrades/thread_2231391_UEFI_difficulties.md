---
title: "UEFI difficulties"
date: 2014-06-25
forum: Installation &amp; Upgrades
---

### Post by phil-stephenson on 2014-06-25
Hi everyone!

I was directed to this forum from the community UEFI help page after having a problem booting to a newly installed Ubuntu 14.04 instance. The culprit computer came with Windows 8. My first attempt was to simply install Ubuntu 14.04 Server amd64. After installing and not being able to boot, I went to the bios settings and looked for the option to turn off UEFI but could not find it. I then followed the instructions on the UEFI community page: I burned a LiveCD (14.04) and booted up into that and ran the installation from there. After rebooting I was still not able to boot up. Next step: booted into the LiveCD environment again, ran the Boot-Repair utility, used it's recommended settings and here was the results of the utility:

[http://paste.ubuntu.com/7696792/](http://paste.ubuntu.com/7696792/)

Again, after rebooting I was unable to boot into Ubuntu. The error message reads:

"Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"

I am NOT trying to dual boot here. I simply want a clean, Ubuntu 14.04 server install and I don't care about the windows data at all. In fact I'd prefer it to be gone!

Any help here would be appreciated, and if more information is needed I can try to provide as much as possible.

Thanks in advance!

---

### Post by oldfred on 2014-06-25
What computer & model.
Many vendors have modified UEFI to only boot the entry with Windows description. And there are mulitple work arounds for those systems.

It looks like Boot-Repair converted install from UEFI to UEFI with secure boot by adding the signed kernel versions. So it should boot with secure boot on or off.

Not required but it is now better to have a smaller / (root) partition of about 20 or 25GB and use rest of drive for /home or data partition(s). When drives were a lot smaller or dual booting where Ubuntu only got 10 to 50GB then a single / default install made sense. But now with TB sized drives an extremely large root is not recommended.

I suggest renaming shim to bootx64.efi or using rEFInd as better options. Others also seem to work at least for some systems.

       [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming  /EFI/Boot/bootx64.efi  to be shimx64.efi or grubx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

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

---

### Post by phil-stephenson on 2014-06-25
Hi oldfred,

Thank you for the quick response. The computer in question is a Gateway DX4870-UB2C ([http://www.pcworld.com/product/1253473/dx4870-ub2c.html](http://www.pcworld.com/product/1253473/dx4870-ub2c.html))

I will certainly take your advice on partitioning off /home.

Regarding renaming shim, just to be specific:
phil@Phil-Ubuntu:/media/phil/Ubuntu-Server 14.04 LTS amd64$ find . -name shim
./pool/main/s/shim

Are you suggesting renaming this file to bootx64.efi ?

The other post suggests renaming /efi/boot/bootx64.efi to grub, but this file already seems to exist:
phil@Phil-Ubuntu:/media/phil/Ubuntu-Server 14.04 LTS amd64$ ls EFI/BOOT/
BOOTx64.EFI  grubx64.efi

Thanks again, and hi from Chicago city proper!

---

### Post by oldfred on 2014-06-25
The system boots from efi partition, so you have to rename files in that partition. Files elsewhere on system are original downloads or backups and should not be modified.

Backup efi partition and copy shimx64.efi (UEFI secure boot) or grubx64.efi (UEFI) into /efi/Boot. Then rename bootx64.efi and change name fo shim or grub to bootx64.efi.

You may be able to use the option D: where in UEFI you change the description of shim to have the expected Windows name so UEFI works. Not sure all vendors look for exactly the same name, but that seems to be the way they have modified UEFI.

Only seen one or two users with Gateways. And they seem to have a more limited UEFI even less features than HP or Sony.

---

### Post by phil-stephenson on 2014-06-25
I was able to get this working after using a bootable USB for Ubuntu server. Upon booting up I brought up the boot menu and choose the non-UEFI version of the USB and went through the installation.

Thanks for the help.

---

