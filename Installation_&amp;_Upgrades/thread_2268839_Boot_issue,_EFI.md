---
title: "Boot issue, EFI"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by michaelbreen85 on 2015-03-11
I have a fresh install of 14.04 on a new SSD. Everything was running fine until I ran boot-repair for some reason that I cannot remember. Now when I boot up I get the following errors: 

Failed to open \EFI\Microsoft\Boot\grubx64.efi - 80000000000000E
Failed to load image
Failed to open \EFI\Microsoft\Boot\MokManager.efi - 80000000000000E
Failed to load image
Failed to open "\EFI\BOOT\fallback.efi": 14
Failed to open \EFI\BOOT\grubx64.efi - 80000000000000E
Failed to load image
Failed to open \EFI\BOOT\MokManager.efi -80000000000000E
Failed to load image

This new HDD has never had Windows installed, so is it possible that boot-repair added those files? Can I simply delete them? 

Boot info shows the following:
Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootx64.efi

Here is a link to the full boot info- [http://paste.ubuntu.com/10583113/](http://paste.ubuntu.com/10583113/)

Thanks for the help.

---

### Post by Mike_Ohlhausen on 2015-03-12
Not much help here, just wondering why there would be a fat32 filesystem for a /boot. The one thing I keep wondering is if the EFI is the same as on my Intel Server board... If there is nothing it can find to boot, it uses EFI from the motherboard to go into some useless try to fix it mode. (well, useless for my level of non-expertise) There should be a boot loader on the MBR, of somesort. If you have no Win gonna be on here, just let it install Grub for a bootloader in the MBR is what I would try. Actually, I always used Grub for a boot loader even for dual booting...

---

### Post by oldfred on 2015-03-12
An efi partition is not a /boot partition. Most desktops do not even need a /boot and leave /boot inside / (root). Some server configurations and those desktops with LVM need /boot partitions.

Older versions of Boot-Repair copied grub into the Windows efi folder and renamed the Windows efi  boot file and then renamed grub to be the Windows efi boot file. That was because many vendors have modified UEFI to only boot Windows by description in UEFI. So that work around did work until Windows or grub updated and files got out of sync again.
If you only have Ubuntu you can copy grub into a Windows folder and boot that way. Windows will never overwrite the Windows named file, but grub updates will not replace it either.

A more common fix now is to use UEFI boot entry for the hard drive which is /EFI/Boot/bootx64.efi. That can be renamed and made to be grub. System will 'allow' you to boot hard drive which then really is grub. Again grub updates will not update that copy and later cause issues if grubversions change.

If only booting Ubuntu, the preferred work around is just to rename the ubuntu entry in UEFI to Windows. Systems sees Windows entry but boots grub. Then updates to grub in efi partition will still be the default entry in UEFI.

You show default boot is the hard drive entry which uses bootx64.efi. But that file could actually be an original bootx64.efi, grubx64.efi or shimx64.efi.

```
BootOrder: [COLOR=#ff0000]3003[/COLOR],3001,3004,2001,2002
Boot0000* Notebook Hard Drive    BIOS(2,500,00)................-.`.......`.A.`........................................
Boot0001* ubuntu    HD(1,800,100000,3c6d1212-54d5-4b03-8eb6-680c74425f10)File([COLOR=#ff0000]EFIubuntushimx64.efi[/COLOR])
Boot0002* Internal CD/DVD ROM Drive    BIOS(3,500,00)................-.g.......g.A.g........................................
Boot0003* Windows Boot Manager    HD(1,800,100000,3c6d1212-54d5-4b03-8eb6-680c74425f10)File([COLOR=#ff0000]EFIMicrosoftBootbootmgfw.efi[/COLOR])RC
Boot0004* Ubuntu    HD(1,800,100000,3c6d1212-54d5-4b03-8eb6-680c74425f10)File(E[COLOR=#ff0000]FIubuntugrubx64.efi[/COLOR])RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC
Boot[COLOR=#ff0000]3003[/COLOR]* Internal Hard Disk or Solid State Disk    RC
Boot3004* Internal Hard Disk or Solid State Disk    RC
```

I would fully backup efi partition, so you can restore anything if needed.

And then test what boots from UEFI menu which should be same as the efibootmgr -v entry shown by Boot-Repair above.

What brand/model computer. Some will let you directly boot ubuntu entry.

To houseclean entries that do not work you must first remove folder in efi partition as UEFI keeps adding entries it finds in efi partition. Then delete entries in UEFI as it remembers them in its NVRAM.

       Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by michaelbreen85 on 2015-03-15
Thanks for the replies. I have tried to change my boot order via efibootmgr -o, but it does not remember the changes on a reboot. Otherwise, I'm not too sure what you are telling me to do Oldfred. Consider me to be somewhere in the intermediate level of users here.

---

### Post by oldfred on 2015-03-15
I would think this which is in the link in my signature as the most common fix for those dual booting Windows with a Vendor UEFI that only boots Windows.

       A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot

   Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi Then boot harddrive entry in UEFI menu.
Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)

   From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.

   sudo mount /dev/sda1 /mnt
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup

   make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

   More examples of users who manually moved efi files
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

---

### Post by michaelbreen85 on 2015-03-16
I am not dual booting though. Windows has never been installed on this harddrive, nor do I plan on running it. Do I still need the windows bootloader files?

---

### Post by oldfred on 2015-03-16
If you do not have Windows at all, you still  can rename bootx64.efi.
 You can just rename the ubuntu entry for grub or shim to read Windows so UEFI internally still checks you are booting Windows entry but it really is grub. 

         C: Use efibootmgr if only Ubuntu, not dual boot, install to make Windows UEFI description boot grub or shim file
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

If you have Windows or later re-install Windows, to restore Windows boot entry:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

---

### Post by michaelbreen85 on 2015-03-16
So it appears that efibootmgr forgets any changes made upon reboot when using -c. Changes will only work for the next boot using -n however. As it stands, the system will boot into Ubuntu, but will first show the errors in the OP. However, when I change the boot order to 0001, 0002, 0003 it will boot cleanly without the error message. Walk me thru how to either change the boot order permanently or get rid of those error messages. The computer is an HP Pavilion d6, and by reading other user's problems with efibootmgr, that seems to be relevant info.

---

### Post by oldfred on 2015-03-16
As near as we can tell, HP and others internally modify UEFI to look for the Windows description. A one time boot entry, or booting the hard drive entry still work. But the UEFI standard of setting any entry as default will not work.

You need to rename or move files, so it thinks it is booting Windows or the hard drive as posted above.

Ubuntu even has  a policy statement against what these vendors are doing in using Windows description. It seems to me to be a total violation of the UEFI spec.
 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

