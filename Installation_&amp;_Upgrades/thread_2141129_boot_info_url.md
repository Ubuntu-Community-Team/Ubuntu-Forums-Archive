---
title: "boot info url"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by ub100 on 2013-05-01
Hi,

I tried installing Ubuntu alongside Windows 8, no boot munu comes up when booting. The install said it was complete then no boot menu. Here is the boot info url [http://paste.ubuntu.com/5624118/](http://paste.ubuntu.com/5624118/) . Does anyone know what the fix is? Both are 64 bit installs in legacy mode, on a modern board with uefi and bios/egacy mode options. Quick start etc are disabled.

Cheers

---

### Post by ub100 on 2013-05-01
The recommended repair asks me to copy and pste this in the terminal  
sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda5" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub*-common shim-signed

when I type y and then enter nothing happens, it does not do grub removal.

It says - chroot: failed to run command `apt-get': No such file or directory

---

### Post by oldfred on 2013-05-02
Boot-Repair is trying to uninstall the efi version of grub, so you can reinstall the BIOS version grub-pc. I do not see a core.img which would show the grub-pc version was correctly installed.

Not sure why you are getting error, but have you booted Boot-Repair in UEFI mode. You need to be booting in BIOS mode or boot any live installer in BIOS mode and reinstall grub2 to MBR.

If boot repair does not work you can do a full chroot and run the reinstall of grub2.

I like kansasnoob's version as it is one line to copy, but his uses sda3 which you must change before copying. Only if it does not work then you have to run each line to see what fails.

 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

      
 Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2 info & full chroot version - also METHOD 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by ub100 on 2013-05-02
Hi,

Thanks for your reply. Does this part not need fixed 

sdb1: __________________________________________________________________________      
File system:       vfat     Boot sector type:  FAT32     Boot sector info:  According to the info in the boot sector, sdb1 starts                         at sector 0. But according to the info from fdisk,                         sdb1 starts at sector 16.


Just to make sure how do I tell if my ubuntu install is in legacy mode before I try your solutions. Would I be able to check that by running a command on the live cd?

---

### Post by oldfred on 2013-05-02
I have seen that before and with the efi partition it does not seem to be critical. With Windows NTFS boot partitions it is critical and fixed with chkdsk from a Windows repair console or repairCD. I would try that on your FAT32 partition, run chkdsk from Windows.
Windows partitions have the same partition start & size info in the PBR or partition boot sector (used by BIOS) as the partition table. If they do not match you cannot BIOS boot with Windows. But you really are not BIOS booting so system is not reading PBR.

---

### Post by ub100 on 2013-05-02
Hi,

You wrote "I have seen that before and with the efi partition", does that mean my ubuntu install boots in efi, if so I will need to change that because windows 8 is installed in legacy/bios mode. How do I tell what mode ubuntu is installed before I try your  solutions. Would I be able to check that by running a command on the  live cd? In bios Other pci device ROM priority is set to UEFI OpROM, should it be set to Legacy OpROM since all other BIOS are set to Legacy?

---

### Post by oldfred on 2013-05-02
Your sdb1 is your installer flash drive?
So that definitely does not matter. The installer will boot in either BIOS or UEFI mode if you system supports both.

---

### Post by ub100 on 2013-05-02
I installed from the live cd, to the drive windows 8 is installed on.
My system supports BIOS and UEFI but windows 8 is installed in BIOS mode, so Ubuntu has to be installed in BIOS mode too, is that right? Can you tell from the boot info url [http://paste.ubuntu.com/5624118/](http://paste.ubuntu.com/5624118/) if Ubuntu is installed in BIOS mode?

---

### Post by oldfred on 2013-05-02
At some point you had grub installed as you have a grub.cfg. But you do not have an efi partition with grub's files nor grub in the MBR nor core.img which it has when installed.

I think you just need to do this:

>  Recommended-Repair
This setting would purge (in order to fix packages) and reinstall the grub2 of sda5 into the MBRs of all disks (except USB without OS).
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s



---

