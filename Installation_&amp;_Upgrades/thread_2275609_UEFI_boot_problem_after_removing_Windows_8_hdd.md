---
title: "UEFI boot problem after removing Windows 8 hdd"
date: 2015-04-27
forum: Installation &amp; Upgrades
---

### Post by alexander-varchenko on 2015-04-27
Hi people, can anyone help me to figure out how to fix this boot problems.
I have hp 4730s laptop with uefi support. I had dual boot installation (windows 8.1 + ubuntu) for some time, but now I removed windows hdd but my boot menu wont works anymore.
I have to start ubuntu from bios boot menu manually: UEFI boot - > bla...
Otherwise it falls to PXE/whatever  boot with message I have not boot loader on my HDD.

I tried to run BootRepair, but no luck, here is saved log form it:
[http://paste.ubuntu.com/10910917/](http://paste.ubuntu.com/10910917/)

---

### Post by oldfred on 2015-04-27
Your fstab shows the efi partition so you are now configured to boot in UEFI mode. 
But you also have a grub in the MBR for CSM/BIOS boot. Was that how your dual booted before? HP's amoung others are not Linux friendly. They modify UEFI to look for "Windows" in the UEFI boot menu entry. That is not per UEFI.

If only booting Ubuntu. You can just change description of Ubuntu entry to Windows. You may need to delete the current Windows UEFI entry & the /EFI/Microsoft folder in the efi partition. Usually best to have secure boot off, but should work with it on, if you use shim not grub in command below.

       C: Use efibootmgr if only Ubuntu, not dual boot, install to make Windows UEFI description boot grub or shim file
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

If you have Windows to restore Windows boot entry:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"


 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by alexander-varchenko on 2015-04-27
Thanks, at first I was very nervous over efi boot procedure )) I deleted windows stuff and tried to set:
>  sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"
It wasn't succeed - > sudo efibootmgr -v discovered it was not created new item.
I was able though to remove windows items with
> sudo efibootmgr -b x -B 
After reboot it hanged again and showed wrong items in the efibootmgr -v. But this time auto-correct option somehow helped.
 And now I can boot it.

> storm@jet:~/Downloads$ sudo efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0001,0002
Boot0000* Notebook Hard Drive    BIOS(2,0,01).......................................................................
Boot0001* Notebook Upgrade Bay    BIOS(3,0,01).......................................................................
Boot0002* Notebook Ethernet    BIOS(80,0,01)..&.....................+..............................................
Boot0003* Notebook Ethernet    BIOS(80,0,01)..&.....................+..............................................


---

### Post by oldfred on 2015-04-27
Those all look like BIOS boot options not UEFI??

Did you boot Ubuntu installer in UEFI boot mode, the first time? 
Only in UEFI mode do you have efibootmgr?

---

### Post by alexander-varchenko on 2015-05-01
I'd say it surprising, cause it auto removes my created item with linux on reboot however there is no issue with autoboot.
At first I thought it boots in BIOS mode, but this check shows "EFI boot on HDD":
> 
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 


---

