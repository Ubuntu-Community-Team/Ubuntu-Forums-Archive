---
title: "Windows 8.1 overwrites the changes done by me into BIOS boot order"
date: 2015-01-11
forum: Installation &amp; Upgrades
---

### Post by ashu2 on 2015-01-11
[COLOR=#333333][FONT=UbuntuRegular]I am trying to have dual boot in my desktop so that i can login into Windows 8.1 or Ubuntu Linux. Everything is working fine except something very strange is happening. In my BIOS - boot order is getting changed by Windows. Even if i make it load ubuntu first and then Windows bootloader. Very first time it works...it loads ubuntu....later if i opt to go for windows(adter making the choice during GRUB screen)...it loads windows but after restart.....windows simply changes that sequence such that windows boot manager will be loaded first and then ubuntu....On the contrary if i choose Ubuntu at the time of GRUB screen it works gracefully doesn't kicks out Windows from the boot loader. It seems windows doens't want to live peacefully with other OSs.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Windows should not be updating the BIOS settings at the first place. Some Background: I installed Ubuntu 14.10 LTS on a partition of the hard disk drive connected to my HP desktop. Secure boot is disabled; fast boot is disabled; legacy boot is enabled. Also changed the behavior of power button in the control panel. In fact followed each and every recommendation in the askubuntu forums. When I boot Ubuntu and restart within Ubuntu, grub-efi lets me choose whether I want Ubuntu or Windows. However, if I go back to Windows and restart, Windows always changes my boot order, placing ubuntu last in the list. I always have to manually modify my UEFI settings and place Ubuntu ahead of Windows if I want to go back to Ubuntu. This seems like too much work. Is there any way to keep Windows from doing this?[/FONT][/COLOR]

---

### Post by oldfred on 2015-01-12
I doubt it.

HP modifies UEFI to only boot Windows or an entry with Windows in description, but will also boot a hard drive entry. And Windows syncs its BCD with UEFI. It used to be only on maintenance, but now seems to be on every reboot.

Several work arounds include adding an entry to BCD in Windows, and modifying the default hard drive entry which is /EFI/Boot/bootx64.efi to really be grub or shim.

       Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)


 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

Some of the alternatives.

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)


 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
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
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

---

