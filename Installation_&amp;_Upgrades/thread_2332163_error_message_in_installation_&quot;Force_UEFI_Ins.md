---
title: "error message in installation &quot;Force UEFI Installation?&quot; ubuntu 16.04"
date: 2016-07-28
forum: Installation &amp; Upgrades
---

### Post by ihab_hamed on 2016-07-28
ubuntu ubuntu 16.04 , i have tried older v but same issue
hp 350 g1
core i5 ram 6G 

I used manual partitioning:
EFI partition 500mg primary beginning,
swap 12gb primary beginning,
/ 50gb primary beginning,
/home 200gb primary beginning.

I only have a new empty Hard Disk 1000gb, there in no dual boot

```

"This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.

If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here.")

```

---

### Post by ubfan1 on 2016-07-29
Maybe a leftover MBR bootloader is confusing the installer.  If there is really no other OS on the machine (other disks?), just force UEFI if that's what you want.

---

### Post by ihab_hamed on 2016-07-29
thank you yes there no other disk and i'm able to force Uefi, but is there away to fix or remove that error ?

---

### Post by oldfred on 2016-07-29
Even if you had Windows in UEFI boot mode, you may still have Windows boot files in the ESP - efi system partition. That is the FAT32 UEFI partition with boot files for all operation systems.

HP is also hard coded to only boot "Windows Boot Manager". That is just a required description. If only booting Ubuntu we modify/add another boot entry that says Windows, but really boots grub's shim file.
Those that dual boot, then have to use a different work around which is to make the fallback or hard drive boot entry in UEFI /EFI/Boot/bootx64.efi to really be  shim. I do not have HP and do this also just to have another boot entry.

Some HP also have a customized boot entry, check if you have that. Details buried in posts here:
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076) 

  Theseusers created the fallback entry:
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 
     
If ESP is not sda1, you have to add parameters for drive & partition in the efibootmgr entry.
 add -p 2 if sda2 etc details on parameters
man efibootmgr
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

