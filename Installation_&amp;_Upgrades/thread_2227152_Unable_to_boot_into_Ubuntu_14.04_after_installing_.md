---
title: "Unable to boot into Ubuntu 14.04 after installing on Windows 8.1"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by Chip_Douglas on 2014-05-31
I'm trying to install Ubuntu 14.04 along side  Windows 8.1. I've disabled secure boot, installed Ubuntu but when it reboots, it boots right into Windows. I don't get a grub menu to select between Windows and Ubuntu. I tried running Boot-Repair from the Ubuntu live USB but it says an error occurred and gave me this URL: [http://paste.ubuntu.com/7555864](http://paste.ubuntu.com/7555864) to share here.  I also turned off fast startup in Windows. Any help would be greatly appreciated.

---

### Post by Chip_Douglas on 2014-05-31
Update: I managed to boot into Ubuntu. Ran software updater. rebooted (went straight back into windows). Booted into Ubuntu again and ran Boot-Repair. Got a new error with a new URL to share: [http://paste.ubuntu.com/7557206/](http://paste.ubuntu.com/7557206/)

It also says: The boot files of [The OS now in use-Ubuntu 14.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to try after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by oldfred on 2014-06-02
Ignore the far from disk error. I have yet to see a UEFI system with that issue. It is for some older BIOS and particularly installs on USB large drives.

HPs just want to boot Windows. Some live with using the one time boot key which seems to work. Others have used one of these alternatives. Several with HP have used the manual move & rename grub or shim file fix.

       **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
A: Manually rename files either bootmfg.efi and/or bootx64.efi : 
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   B:Boot_Repair rename Windows bootmfg.efi. But cannot boot Windows from UEFI only grub 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   C: Edit Windows BCD, one Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   D: If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   E: Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[URL="http://www.rodsbooks.com/refind/secureboot.html"]http://www.rodsbooks.com/refind/secureboot.html

      [/URL]
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)

    [URL="http://www.rodsbooks.com/refind/secureboot.html"]
[/URL]

---

