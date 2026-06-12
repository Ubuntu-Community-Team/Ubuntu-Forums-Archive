---
title: "Installing ubuntu with preinstalled win 8.1 (HP650)"
date: 2015-03-24
forum: Installation &amp; Upgrades
---

### Post by Nadeem_Q._Mehmood on 2015-03-24
[FONT=arial]Dear All,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I am trying to install Ubuntu beside my preinstalled window 8.1, but still I am not able to get its working. The system always boots into windows. [/FONT]
[FONT=arial]After running the boot repair tool, I have this following link, kindly help me how I can fix this problem. [/FONT]

[FONT=arial]The link is [/FONT][URL="http://paste.ubuntu.com/10668534/"]http://paste.ubuntu.com/10668534/
[/URL]
[FONT=arial]specs:[/FONT]
[FONT=arial]HP 650 win 8.1 core i3
ubuntu is installed in EFI mode and secure boot is disabled.[/FONT]
[FONT=arial]I ran the **bcdedit** command  to change the default boot entry of windows boot loader, but no avail.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thank you[/FONT]

---

### Post by ubfan1 on 2015-03-24
Your last "efibootmgr -v" output looks OK, with ubuntu first in the list.  However, HP may do odd things like only boot entries named "Windows Boot Manager" or maybe only boot efi files named bootmgfw.efi instead of shimx64.efi.  Can you directly start the ubuntu from the efi menu of devices/oses to boot?  search this forum for HP issues with UEFI.

---

### Post by Nadeem_Q._Mehmood on 2015-03-24
From win8.1 when I go in BIOS (UEFI settings restart+shift key) it shows me as boot options in the following error:
**Boot Device Options**
[FONT=courier new]  OS Boot Manager
  ubuntu <Hitachi HTS545...A7E380>
  ubuntu <Hitachi HTS545...A7E380>
  ubuntu <Hitachi HTS545...A7E380>
  ubuntu <Hitachi HTS545...A7E380>
  Boot From EFI file
[FONT=arial]
[/FONT][/FONT]Does it mean that my HDD have 4 installations of ubuntu? I did the installations for more than one time but I thought that the installation is on the same derives, so it will replace the previous ones. Also the main device was [COLOR=#000000] /dev/sda[/COLOR] during instalation which is by default. I think I was wrong.  How can I remove the extra ones now.
From these options when I click any ubuntu boot device it starts ubuntu, but not directly. directly it only boots up windows,
regarding file names sorry I could not understand as you explained.
Thanks for your guidance

---

### Post by ubfan1 on 2015-03-24
I think you got to the Windows boot manager from what you posted.  The EFI boot menu is usually displayed when you type a function key or DEL or ESC at power-on (varies by machine).  Sometimes it will only offer HDD, USB, CDROM,net, in which case, selecting HDD may offer additional choices like ubuntu, Windows.  Try ubuntu from that menu.  The first listing in your efibootmgr output is ubuntu, which runs shimx64.efi, so that should work in either secure boot or non-secure boot mode.  Can you mount the FAT EFI partition and see the contents of /EFI/ubuntu?  If the directory has a problem, maybe the bootloader cannot work, so the next entry is tried.  It does look like you have multiple entries for ubuntu in the Windows boot manager, but they really should not affect anything.  The efibootmgr listing is also a little strange -- the Boot0006 Windows entry disappeared from the bootorder, and the 3000 series numbers are new to me.
   Some vendors have done strange things like only allowing certain names for the bootloader to work, and even only allowing certain names in the nvram to work -- the ones that Windows uses.  If that is your situation (and I think HP is one of those vendors from seeing other postings here), you simply rename the shimx64.efi bootloader file to be bootmgfw.efi and change the "ubuntu" label to "Windows Boot Manager" (efibootmgr offers the ability to change labels).  Now boot-repair will do the file rename for you, and that looks like what has been done in /EFI/Boot/bckbootx64.efi, maybe leaving a copy of grubx64.efi as bootx64.efi (you can only tell from the file sizes).  The bootloader /EFI/Boot/bootx64.efi is a good one to  replace, since if your first bootloader in order  fails, it may be tried even before the bootloader next in order.  I like to replace bootx64 with shimx64 and leave a copy of grubx64 in the same directory so it will work regardless if secure boot is enabled or disabled.
  I think you probably only have one ubuntu installation on disk, with multiple boot entries to it.  You can tell what is mounted as root when running them.

---

### Post by oldfred on 2015-03-25
Every HP we have seen, seems to need one of several work arounds to boot Ubuntu. 
They modify UEFI to look for the Windows description and only allow direct boot of that entry. 
But you can directly boot a hard drive entry which is bootx64.efi or indirectly boot thru Windows. Windows can reset UEFI to one time boot entry and use the ubuntu as a one time entry and that seems to work for many users.

       HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

            HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

    
 Backup entire efi partition before making changes.

   A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot

   Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi Then boot harddrive entry in UEFI menu.
Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)

   From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.

   sudo mount /dev/sda1 /mnt

   only if /EFI/Boot not already existing, run the mkdir command,
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot

   If new folder created, the bootx64.efi will not exist, skip backup command

   sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup

   make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.

   sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi
Then you should be able to boot hard drive entry in UEFI menu.

   More examples of users who manually moved efi files
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

---

