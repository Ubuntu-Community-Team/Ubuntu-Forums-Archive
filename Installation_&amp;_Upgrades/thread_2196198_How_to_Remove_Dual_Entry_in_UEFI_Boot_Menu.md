---
title: "How to Remove Dual Entry in UEFI Boot Menu"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by drseuss2 on 2013-12-28
I installed Ubuntu 13.10, and it was installed properly. It, however, created two entries in boot menu. Both are named as "ubuntu", and one is not working, which means I can't boot from one "ubuntu" entry. I would like to remove the non-working boot-entry since they have the same name, and I don't know a way to distinguish them in boot menu. 

my 

[I]$ efibootmgr -L sda 
[/I]
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0006,0001,0000,0004,0005
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0004* UEFI: IP4 Realtek PCIe FE Family Controller
Boot0005* UEFI: IP6 Realtek PCIe FE Family Controller
Boot0006* ubuntu

$ efibootmgr -L sda -v 

BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0006,0001,0000,0004,0005
Boot0000* Windows Boot Manager	
Boot0001* ubuntu	File(\EFI\ubuntu\shimx64.efi)
Boot0004* UEFI: IP4 Realtek PCIe FE Family Controller	
Boot0005* UEFI: IP6 Realtek PCIe FE Family Controller
Boot0006* ubuntu	(\EFI\Ubuntu\grubx64.efi)

Which entry should I remove? boot0001 or boot0006 ?
Would there be any adverse effects?

---

### Post by oldfred on 2013-12-28
Do you have secure boot on? Then the grub entry is probably the one not working and only shim works. Otherwise I thought both should work.

You can add, change & delete with efibootmgr. Often better to use UEFI/BIOS if you have the capability in it, but not all build in the capability.

       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
change label
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)

   Users are recommended to try bcfg only if efibootmgr fails to create working boot entries in their system. 
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#bcfg](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#bcfg)

And some systems with Windows 8 or 8.1 see to auto reset Windows as first entry every time you boot Windows.
      
 Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by drseuss2 on 2013-12-28
Thanks for your reply, oldfred. 

I have UEFI on. I tried removing the [COLOR=#000000]grubx64.efi with[/COLOR]

$ efibootmgr -b 6 -B 

, but it reappears after reboot.

---

### Post by oldfred on 2013-12-28
It may just be as long as file is there UEFI rediscovers it? I am not sure you should remove it although shim is really the grub version being used.

---

