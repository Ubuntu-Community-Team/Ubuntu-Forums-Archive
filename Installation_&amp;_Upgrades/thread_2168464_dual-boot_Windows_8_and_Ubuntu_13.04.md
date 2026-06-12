---
title: "dual-boot Windows 8 and Ubuntu 13.04"
date: 2013-08-17
forum: Installation &amp; Upgrades
---

### Post by peabody81 on 2013-08-17
After I installed 13.04, I was only able to boot into Windows 8. Ran boot-repair, was then able to boot into 13.04, but no longer could boot into Windows, when attempting to boot got "Preparing Automatic Repair" and computer would hang. Ran boot-repair again, obviously didn't know what I was doing, now computer will not boot at all, don't get Grub menu. Here's my Boot Info URL - [http://paste.ubuntu.com/5998287/](http://paste.ubuntu.com/5998287/)

---

### Post by oldfred on 2013-08-18
Moved to your own thread as your issues are somewhat different.

If you go into UEFI menu can you not choose ubuntu? It looks like you originally installed Ubuntu in BIOS mode where Windows is in UEFI mode. Both have to be same mode to easily dual boot. And you have to set in UEFI/BIOS what system you want to boot.

It looks like Boot-Repair has a bug. It recently changed from automatically making backups of Windows files and using those to boot.  The boot stanza in 25_custom is wrong and you need to fix it. Remove the [COLOR=#ff0000]bkp[/COLOR] or the reference to the backup version which does not exist in your install currently.

Your Windows boot file:/EFI/Microsoft/Boot/bootmgfw.efi 

Your menu entry:
  
```
 menuentry "Windows UEFI [COLOR=#ff0000]bkp[/COLOR]bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 8C82-899E
chainloader (${root})/EFI/Microsoft/Boot/[COLOR=#ff0000]bkp[/COLOR]bootmgfw.efi
}

```
If from live installer you have to mount the partition with 25_custom.  If from working install you do not. You can only run the sudo update  grub command from inside your working install.
From live installer:
sudo mount /dev/sda5 /mnt
 sudo cp -a /mnt/etc/grub.d/25_custom /mnt/etc/grub.d/bkup25_custom
gksudo gedit /mnt/etc/grub.d/25_custom
#Then do this only after booting into your working install:
sudo update-grub



From working install.
       sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
#Then do:
sudo update-grub

---

### Post by YannBuntu on 2013-08-18
(for info: [https://bugs.launchpad.net/boot-repair/+bug/1213600](https://bugs.launchpad.net/boot-repair/+bug/1213600) )

EDIT: you used Boot-Repair v3.198~ppa16. Please could you check if the bug is still present with the latest version:
1) boot on your Boot-Repair-Disk, choose 'Try Ubuntu'
2) close the Boot-Repair windows that will automatically appear
3) connect internet
4) update the 'boot-sav' package
5) run Boot-Repair, click "Recommended Repair"
6) indicate the new URL that will appear

thank you

---

### Post by YannBuntu on 2013-08-18
I double-checked the code, and I see no possibility for this to be a bug in Boot-Repair, because B-R systematically deletes the 25_custom file, and then creates a new one with exactly the name of the EFI files it finds in the ESP.
I'd rather bet the Windows EFI files have been restored (renamed without 'bkp') by the Windows "Automatic Repair":

> **peabody81 said:**
> when attempting to boot got "Preparing Automatic Repair" 

peabody81, please could you simply run the Recommended Repair again, and indicate the new URL that will appear?

---

### Post by peabody81 on 2013-08-18
OK, played around with some of the options in boot-repair, I am now getting the GRUB menu, can boot into Ubuntu, but still can't get Windows to boot. Here's my info:
[http://paste.ubuntu.com/6001155/](http://paste.ubuntu.com/6001155/)

---

### Post by oldfred on 2013-08-18
You show both of these in your efi partition.
                        /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 

Boot-Repairs rename changes grub2's shim file which has the Microsoft signing key to be the bootmgfw.efi file for those UEFI systems that have a hard coded UEFI to only boot that file. Then from grub menu you can boot the bkpbootmgfw.efi or original Windows file to boot Windows. Does that not work?
Did you turn fast boot off in Windows? 

From line 1072 in BootInfo report.

 Save and rename /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi)
cp /boot/efi/EFI/ubuntu/grubx64.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
df /dev/sda2

---

### Post by peabody81 on 2013-08-18
Selecting bkpbootmgfw.efi from the Grub menu causes Windows to hang on the "Preparing Automatic Repair" screen. Selecting Windows Boot UEFI loader doesn't do anything, I get a black screen, then right back to Grub menu. I don't believe I turned off Fast Boot in Windows.

---

### Post by oldfred on 2013-08-18
It is important to turn fast boot off. A few early systems from one vendor could only be fixed by replacing motherboard. There was no way to get back into UEFI menu to fix anything.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)


 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

Black screen can just be a video system issue. Have you added nomodeset to grub linux boot line? 
What video card/chip do you have?
      
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by peabody81 on 2013-08-19
Turned off Fast Boot via the BIOS setup menus/screens. Re-ran boot-repair, latest log is [http://paste.ubuntu.com/6004918](http://paste.ubuntu.com/6004918)  Same results as before, Selecting bkpbootmgfw.efi from the Grub menu causes Windows to hang on the "Preparing Automatic Repair" screen. Selecting Windows Boot UEFI loader doesn't do anything, goes right back to Grub menu

---

### Post by oldfred on 2013-08-20
You may need to undo the file rename that Boot-Repair has done, so you can directly boot into Windows and then fix Windows from its repair console. You can only boot a working Windows that is not hibernated or needing chkdsk from grub menu.

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by peabody81 on 2013-08-20
I must not have clearly communicated my issue. I cannot boot into Windows at all, I did as you suggested above, now I can't boot at all, don't get the GRUB menu. [http://paste.ubuntu.com/6008063](http://paste.ubuntu.com/6008063). What happens now is I go straight to the "Preparing Automatic Repair" screen, which never does anything, just sits there displaying that message. Can I un-do what I just did by un-checking the "restore EFI backups" option in boot-repair?

---

### Post by oldfred on 2013-08-20
UEFI controls booting choices. I cannot tell from Boot-Repair which choice in UEFI you are using. If booting the Windows entry in UEFI mode then Windows needs repairs from a Windows repairCD or flash drive if you cannot get it to run its own repairs. 

If you do not have settings correct in UEFI, such as trying to boot Windows in CSM mode then it would be expected that it would fail. 

You can restore the Windows boot file with the undo command, but it seems like you already are booting Windows? I would try the undo.

---

### Post by Lim_Xiang_Yann on 2013-08-21
wait, did i just saw Windows Vista in sdb?

---

### Post by oldfred on 2013-08-21
That was just the PBR - partition boot sector. NTFS PBR has different configurations for each version of Windows to know what to boot, but it is not showing any boot files. All NTFS partitions have to have the boot signature  even if data. But not used unless booting.

All of sdb is MBR(msdos) partitioned, so nothing will boot from a UEFI boot. The old Ubuntu install may boot if UEFI changed to BIOS mode and the old install has its boot in the MBR, but syslinux is in MBR now.

---

