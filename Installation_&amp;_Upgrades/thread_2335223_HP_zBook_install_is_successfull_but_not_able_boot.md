---
title: "HP zBook install is successfull but not able boot"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by arjun20034 on 2016-08-26
trying to install ubuntu 16.04 on a zBook, it had windows on it which  was wiped completely. I tried installing in secure mode, UEFI with  compatibilty and legacy mode. All three just say "No bootable image  found".  Breaking my head since a week, any help is appreciated.
I get a error message saying bootable image not found when i try to boot, I followed [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to the T.

Here is the paste 2 from boot repair

[http://paste2.org/Ew1PjeCp](http://paste2.org/Ew1PjeCp)

After the repair I could to this once:
I can see the OS installed correctly and I can boot to it if manually go  to boot options and select ubuntu from the list. This loads Grub menu  where I can select ubuntu. But if I just let the laptop boot, it says no  boot image found.

---

### Post by mook765 on 2016-08-26
It looks like you installed several times.
First you installed in legacy-mode, that wiped Windows, but not completely, some files on the ESP were left. The partition-table was damaged as well.
The installation was not bootable, so you tried to install again, this time in UEFI-mode.(I say it looks like, only you know exactly...)
I am not sure, if it is possible to repair that, you would have to repair the partition-table, and you would have to remove the WIndows-bootloader manually from the ESP.
Normally there is a backup of the partition-table at the very end off the disk, but it could be a back-up off an already damaged partition-table, I am really not sure for that.
The easy solution is to start over, wipe the disk totally create a new partition-table, create a new ESP and then install. Then you just make sure to boot the installation-media in UEFI-mode.
Repairing might be another week off headache, maybe two...
Another quick solution would be to change the boot-order in UEFI-Bios.  But the result would be far away from a clean install and may lead to  problems in the future, i would not recommend this.
Let's wait what our gurus say, i am pretty young in this business...
Don't worry, its not a hardware-damage...

---

### Post by oldfred on 2016-08-26
HP is not UEFI dual boot or boot anything other than Windows friendly. You have to do work arounds to make it work.

Current Report shows mount of efi system partition (ESP) in fstab, so it currently is UEFI boot.
But you have grub in MBR for BIOS boot left over, and it looks like two bios_grub partitions, sda2 & sda4. I have never seen that, but if you want BIOS boot delete one or the other. And then use Boot-Repair to install BIOS version of grub.

If you want UEFI boot you need to run Boot-Repair's advanced mode.
       
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)

Others with HP manually created /EFI/Boot and manually copied shimx64.efi to bootx64.efi. The bootx64.efi is a hard drive or fallback boot entry. Not sure if hard drive entry currently in UEFI will boot that or you need to add another entry to UEFI. But ubuntu entry in UEFI will not boot. 
HP violates UEFI spec that says not to use description as part of boot. And only valid description is "Windows Boot Manager". 
Since not using Windows, the other work around is to change description of "ubuntu" entry that boots shimx64.efi to the Windows description. Then it will boot grub using a Windows UEFI entry.

        Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 
    Some HP do have a way to boot, but buried pretty deep.
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file) 
      
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 
    
 You may have to delete current Windows entry in UEFI first:
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1. 
     sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by arjun20034 on 2016-08-27
Thank you so much, oldFred!, re installed after wiping everything and copied the ubuntu efi files to microsoft and the boot folders and it works! :)

---

### Post by oldfred on 2016-08-27
Glad that worked, you can change to Solved so others that search forum may find this thread.

---

