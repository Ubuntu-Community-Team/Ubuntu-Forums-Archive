---
title: "Dual boot/grub problem after installing Ubuntu"
date: 2020-12-17
forum: Installation &amp; Upgrades
---

### Post by stevenp1 on 2020-12-17
[FONT=arial][SIZE=2]Hello,

I am new to Ubuntu. I have installed version 20.10 to run alongside Windows 7 that was already installed and I would like to be able to dual boot, ideally to have the option of selecting Windows or Ubuntu when booting.

While installing Ubuntu an error was generated indicating that the installation of grub failed.

I restarted the PC but was unable to boot into either Windows or Ubuntu.

I changed the BIOS to enable UEFI and was then able to boot into Ubuntu although the message "System BootOrder not found" is displayed. I ran the Boot Repair as advised on the following url;
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I selected the Recommended Repair option. It prompted me to run the following commands, which I did 
sudo chroot "/mnt/boot-sav/sda7" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda7" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda7" apt-get purge -y grub*-common shim-signed

Once done , I clicked the forward button, the message "GRUB is still present. Please try again" was returned.
I clicked Cancel. I then took the option to Create a boot summary, which can be found at the following url:
[https://paste.ubuntu.com/p/GqCrvj6rfF/](https://paste.ubuntu.com/p/GqCrvj6rfF/)[/SIZE][/FONT]

Any help would be greatly appreciated.

Many thanks

Steve

---

### Post by yancek on 2020-12-17
The default for windows 7 is to install in Legacy mode rather than EFI which is the case with your computer.  You installed Ubuntu EFI as shown with partition sda6 beginning at line 45 of boot repair.  The Ubuntu Grub bootloader installed EFI will not boot a legacy installation of windows.  You also have Grub installed to the MBR of that disk which would not be necessary with an EFI install.  Delete sda6 and reinstall and make sure you do not install in EFI mode.  You could actually delete sda6 and sda7 and then create a partition using that space for Ubuntu.  

The exact error you got regarding grub failing during the install would have been useful.  If you enabled UEFI to boot Ubuntu then disable it before running the installer again.  The installer should show a purple screen on boot if you are booting Legacy.

---

### Post by CelticWarrior on 2020-12-17
> [COLOR=#000000]The installer should show a purple screen on boot if you are booting Legacy.[/COLOR]
It used to but that's no longer the case.

---

### Post by oldfred on 2020-12-17
You cannot have an old Windows BIOS/MBR install and newer UEFI install on same drive.
Best to always have all systems installed in same boot mode.
But also best to have UEFI installs, if hardware is UEFI.

Windows requires boot flag on primary NTFS partition with its boot files. Your sda1.
But UEFI requires boot/esp flags on ESP - efi system partition, your sda6. You cannot have two boot flags on one drive.
With gparted from live installer, move boot flag back to sda1.

Boot live installer in live mode & reinstall grub in BIOS boot mode. (looks like that already done?)

Only boot in BIOS mode.
You should plan on installing a current Windows as Windows 7 is EoL - end of life and not getting support anymore. When you get hacked, you not only risk yourself, but everyone else as it can convert your system to a bot hacking others.
And then install Windows in UEFI boot mode to gpt partitioned drive. That will erase drive, so be sure to have good backups of your data.

---

### Post by stevenp1 on 2020-12-18
Hello,

Many thanks for the replies. I have moved the boot flag to sda1 and now see the menu with the option to run Ubuntu or Windows when booting :D. 

I'm not sure if there is a problem still with the GRUB installation. I since tried the following again:

[LEFT][COLOR=#000000][FONT=arial]I selected the Recommended Repair option. It prompted me to run the following commands, which I did [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]sudo chroot "/mnt/boot-sav/sda7" dpkg --configure -a[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]sudo chroot "/mnt/boot-sav/sda7" apt-get install -fy[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]sudo chroot "/mnt/boot-sav/sda7" apt-get purge -y grub*-common shim-signed[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Once done , I clicked the forward button, the message "GRUB is still present. Please try again" was returned.

Thanks

Steve[/FONT][/COLOR][/LEFT]

---

### Post by oldfred on 2020-12-18
I have never run the chroot commands from Boot-Repair.
But a normal chroot command is only issued once & then you issue the other commands.

Several examples of chroot to repair a system.
chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

