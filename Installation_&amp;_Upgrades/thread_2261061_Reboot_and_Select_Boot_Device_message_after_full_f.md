---
title: "Reboot and Select Boot Device message after full format/install from 14.04 live cd"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by Keilan on 2015-01-16
[COLOR=#333333][FONT=UbuntuRegular]Hello everyone,

I'm trying to install 14.04.01 as a fresh OS on my laptop (previously a dual-boot of Windows 8.1 and Ubuntu 13.10). After running the live CD and selecting Install Ubuntu, I went through the whole install process (telling to replace existing operating systems), and on rebooting without the live CD, it gave me a Reboot and select Boot device message. So I loaded up the live cd again and installed the boot-repair tool. I ran this, and after restarting it successfully booted into ubuntu once. However if I restart, I get the "Reboot and select Boot device message" again. I can reproduce this process (run boot-repair from the live CD, boot successfully once, and then fail again upon restarting).
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any advice on how to solved this would be appreciated.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Boot repair gives [this boot info link]("http://paste.ubuntu.com/9760001/").

Thanks![/FONT][/COLOR]

---

### Post by oldfred on 2015-01-16
What brand/model system?

Many systems now have UEFI that only want to boot Windows.
You also have a grub in the MBR for BIOS boot, but without bios_grub partition that will not boot. Make sure you only are in UEFI mode.

Some with just Ubuntu are able to rename grub or shim to be Windows, so the UEFI thinks it is booting Windows. Other create/rename bootx64.efi in /EFI/Boot folder. You currently do not have that folder but can create it.

       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019

      [/URL]
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

 **A:** Manually rename files efi boot files in efi partition

 **a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.


       From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
mount /dev/sda1 /mnt
#only if not already existing, 
mkdir /mnt/EFI/Boot
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi 
     
     [URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by Keilan on 2015-01-16
Thanks for the help!

My system is a Satellite P50-A. It uses UEFI and I have SecureBoot disabled in my BIOS, and it is set to run in UEFI mode. The system originally came with Windows 8.1 which I dual booted with Ubuntu 13.10. This configuration worked fine. I've created a new partition table since then however.

I executed the command you listed as d1 (using efibootmgr), and then performed the mounting steps as you described. And that appears to have done it! I've restarted a few times in a row as a bit of a sanity check, and every time it "Checks for Media" but after that is done, Grub loads and it works fine booting into Ubuntu. I'm going to mark this as solved, thanks a lot!

---

### Post by oldfred on 2015-01-16
Glad that worked. :)

---

