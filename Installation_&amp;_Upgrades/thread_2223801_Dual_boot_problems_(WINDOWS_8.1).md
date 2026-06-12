---
title: "Dual boot problems (WINDOWS 8.1)"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by Lucas_Alvarez on 2014-05-13
Hey everybody, I was trying to install Ubuntu LTS 14.04 64 bits alongside my Windows 8.1 64 bit OS but after finishing the process described here ([http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html?m=1](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html?m=1)), GRUB fails to load on startup. Any ideas?

Here's the boot-repair link: [http://paste.ubuntu.com/7455390/](http://paste.ubuntu.com/7455390/)

---

### Post by oldfred on 2014-05-13
It says it reinstalled grub without error. Not sure what other error Boot-Repair is reporting.

 grub-install /dev/sda: exit code of grub-install /dev/sda:0

Can you boot ubuntu entry in UEFI menu?
BootOrder: 0002,3000,3002,3003,2001,2002,2003
Boot0000* Windows Boot Manager
Boot0001* USB Hard Drive (UEFI) - SMI     USB DISK
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot0002* ubuntu.

      
 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   If Description has to be Windows then change description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

