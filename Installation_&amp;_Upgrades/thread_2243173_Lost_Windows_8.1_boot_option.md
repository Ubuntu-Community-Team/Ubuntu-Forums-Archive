---
title: "Lost Windows 8.1 boot option"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by Piers_Shepperson on 2014-09-06
I have a dual boot Ununtu 14.4 and Windows 8.1 machine, however I can not log on to Windows any more. Seems to have lost Windows 8.1 boot info?!? Guess I could create a new Windows boot, but would really like to rescue old one.

I have used boot-repair a few times details at.
paste.ubuntu.com/8271308, also 5273089,8274706,8274904,8275268. I think 8275628 was the last one.

   History.
 Originally build and install Windows 7 RAID 0 setup with 4HDs,.
 Few mouths.
 Split RAID setup into four different HDs.
 Few mouths.
 Upgrade to Windows 8.1.
 Few mouths.
 Create dual boot with Ubuntu 14. Everything fine :)
 Few mouths.
 Informed HD with Ubuntu boot is about to fail.
 Create second Ubuntu boot on another HD copy files across.
 HD with first Ubuntu 14 instillation packs up -> Can no longer log on to anything.
 Run Ubuntu from CD and run Boot-Repair. -> Can now log on to Ubuntu but not Windows.
 Run Windows8.1 install disk, try to repair Windows boot. Windows 8.1install disk can only find Windows 7 (Originally I thought it was a misprint in error message) Windows 8.1 is hidden. No luck trying to repair.
 

 Oh and following might be relavent.
 

 piers@Ubu:~$ sudo update-grub 
 Generating grub configuration file ... 
 Found linux image: /boot/vmlinuz-3.13.0-35-generic 
 Found initrd image: /boot/initrd.img-3.13.0-35-generic 
 Found linux image: /boot/vmlinuz-3.13.0-32-generic 
 Found initrd image: /boot/initrd.img-3.13.0-32-generic 
 ERROR: pdc: identifying /dev/sdc, magic_0: 0xe1e2e3e4/0x940d0602, magic_1: 0xd9dadbdc/0x0, total_disks: 0 
 ERROR: adding /dev/sdc to RAID set "pdc_ceidiibehe-1" 
 ERROR: removing RAID set "pdc_ceidiibehe-1" 
 ERROR: pdc: identifying /dev/sda, magic_0: 0xe1e2e3e4/0x940d0602, magic_1: 0xd9dadbdc/0x0, total_disks: 0 
 ERROR: adding /dev/sda to RAID set "pdc_ceidiibehe-0" 
 ERROR: removing RAID set "pdc_ceidiibehe-0" 
 Adding boot menu entry for EFI firmware configuration 
 done

Thanks for any help

---

### Post by oldfred on 2014-09-09
It looks like Boot-Repair removed some RAID meta-data. So this may not be required any more.

       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
repeat for all other drives.

You show sda & sdb as MBR(msdos) drives with a Windows BIOS install in sda, but missing boot files in sda1.
You show sdc as a gpt partitioned drive with UEFI booting.

This says Boot-Repair ran the "buggy" UEFI rename. Best to undo that with Boot-Repair. Then Windows should boot in UEFI mode.
      
 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

You sdd drive is a 3TB drive and must have gpt partitioning. Not sure what errors it is having.

What does this show?

 sudo apt-get install gdisk
sudo gdisk -l /dev/sdd

---

