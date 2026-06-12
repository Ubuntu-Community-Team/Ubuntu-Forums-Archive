---
title: "Windows 8.1 won't boot after installing Ubuntu 14.04"
date: 2014-06-24
forum: Installation &amp; Upgrades
---

### Post by Ahmed_Jarboui on 2014-06-24
[FONT=&quot]I have windows 8.1 installed by default when I got my new laptop. I installed Ubuntu 14.04 alongside windows 8. I can easily access Ubuntu but when I try to launch windows 8, nothing happens. Using the Ubuntu DVD, I tried the boot repair code :[/FONT]

  [FONT=&quot] [/FONT]
  [FONT=&quot]sudo add-apt-repository ppa:yannubuntu/boot-repair[/FONT]
  [FONT=&quot]sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"[/FONT]
  [FONT=&quot]sudo apt-get update[/FONT]
  [FONT=&quot]sudo apt-get install -y boot-repair && boot-repair[/FONT]

  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]I got this code from boot-repair [http://paste.ubuntu.com/7676376](http://paste.ubuntu.com/7676376)  [/FONT]

  [FONT=&quot] [/FONT]
  [FONT=&quot]PS: I can access windows 8 folders through Ubuntu interface.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Please I need your help to solve this problem[/FONT]

---

### Post by oldfred on 2014-06-24
It looks like Boot-Repair did its rename of the original Windows file, but did not create the 25_custom boot entry to boot it like it used to??

  /EFI/Microsoft/Boot/bkpbootmgfw.efi 
 /EFI/Microsoft/Boot/bootmgfw.efi 

HP seems to be one of the vendors that modifies UEFI to only boot a Windows entry in UEFI mode. So Boot-Repair would copy shim into Windows boot folder and rename it to be the Windows bootmgfw.efi so UEFI thinks it is booting Windows but really boots grub. But without entry to boo the renamed/backup bkpbootmgfw.efi file you cannot boot Windows.

      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

And other options as work arounds for vendors that do not follow the UEFI standard and make system only boot Windows. I suggest renaming bootx64.efi or use rEFInd.

      
 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming  /EFI/Boot/bootx64.efi  to be shimx64.efi or grubx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

