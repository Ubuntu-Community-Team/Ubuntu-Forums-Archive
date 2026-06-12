---
title: "Problems installing Ubuntu 16.04 LTS on NUC device"
date: 2017-03-27
forum: Installation &amp; Upgrades
---

### Post by draken79 on 2017-03-27
Attempted to install Ubuntu on an Intel NUC device. Each time I install it and try to get it to boot from the device itself, it fails but seems to install correctly on the drive. I know this has something to do with UEFI and the boot sector but at a loss to figure out what to adjust to get this booted properly. I have gone through the boot repair and it produced this link [http://paste2.org/AwtvOWnA](http://paste2.org/AwtvOWnA). Would appreciate if anyone can assist. 

Thanks!

---

### Post by oldfred on 2017-03-27
I have tried helping several with NUC, but do not have one and do not know all the details. Not sure I have really helped.

But with any UEFI system do not mix UEFI & BIOS boot. If you really want BIOS boot from gpt drive, you must add a 1 or 2MB unformatted partition with the bios_grub flag.
But better to use UEFI.

While UEFI may allow more than one ESP - efi system partition, we have yet to see an implementation that will boot with two ESP both active at same time.
You have both sda2 & sda4 as ESP. Remove boot flag from sda4.

Since UEFI, you should not boot in BIOS mode and install grub to gpt's protective MBR. But that is not otherwise used, so ok to leave it, but just never boot in BIOS mode as it will not work.

You still have a /EFI/Microsoft folder and /EFI/Boot folder.
If you run Boot-Repair in UEFI mode, it will backup bootx64.efi and copy /EFI/ubuntu/shimx64.efi to be /EFI/Boot/bootx64.efi. That is a fallback or hard drive boot entry, not the Ubuntu entry. Many systems will boot with that.
Looks like it worked.
> cp /mnt/boot-sav/sda3/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda3/boot/efi/EFI/Boot/bootx64.efi (& .grb)

But you do not have an UEFI boot entry.

UEFI boot defaults to use sda1, so each time you use efibootmgr, you have to use extra parameters to specify drive & partition.
UEFI suggests ESP be first partition, but you made swap first, which will still work.

       sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sd[COLOR=#ff0000]X[/COLOR] -p [COLOR=#ff0000]Y[/COLOR]
sd[COLOR=#ff0000]X[/COLOR] is drive, [COLOR=#ff0000]Y[/COLOR] is efi partition, example for sda2 

    sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sd[COLOR=#ff0000]a[/COLOR] -p [COLOR=#ff0000]2
[/COLOR]
Check that new entry is there without having to run the full Boot-Repair report:
sudo efibootmgr -v

NUC may also only boot Windows. You still have Windows, but can change that to actually boot shimx64.efi. Systems only check description, not actual file used to boot.
You can delete current Windows entry:
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 

Then add a new "Windows Boot Mananger" Entry:
      
 
 **d1**:  If Description has to be Windows then change UEFI description. 

 	sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"  -d /dev/sd[COLOR=#ff0000]a[/COLOR] -p [COLOR=#ff0000]2
[/COLOR]    
Again check that UEFI is updated:
sudo efibootmgr -v

---

### Post by draken79 on 2017-03-29
oldfred, 

Appreciate the very detailed answer. 

Your instructions led me to where I needed to be. I'm not a frequent Ubuntu user but utilize it for signage and maybe to boot to from a Live CD to rescue data from a machine. 

Thank you very much sir.

---

