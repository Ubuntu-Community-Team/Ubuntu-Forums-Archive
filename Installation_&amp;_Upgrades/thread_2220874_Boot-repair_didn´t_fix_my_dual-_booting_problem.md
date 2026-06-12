---
title: "Boot-repair didn´t fix my dual- booting problem"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by abraram777 on 2014-04-29
[URL="http://paste.ubuntu.com/7361975/"]i tried several ways iand i cant get it right..


http://paste.ubuntu.com/7361975/[/URL]

---

### Post by oldfred on 2014-04-29
Can you boot ubuntu entry in UEFI. 
It is shown here.
```
BootOrder: 0000,2002,0001,3001,2001,2003
Boot0001* Windows Boot Manager
Boot0003* Internal CD/DVD ROM Drive (UEFI)
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot0000* [COLOR=#ff0000]ubuntu[/COLOR].
```

But many HPs seem to be the one's where they have modified UEFI to only boot Windows.
But any Windows maintenance will reset Windows to be first in boot order.

Some things to try:
 **Systems that only boot Windows from UEFI. Often Sony & HP**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   Some install rEFInd which seems to be another workaround.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

