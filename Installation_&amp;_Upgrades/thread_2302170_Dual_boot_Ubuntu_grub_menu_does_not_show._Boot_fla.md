---
title: "Dual boot Ubuntu grub menu does not show. Boot flag issue?"
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by haffer on 2015-11-08
Hi guys,

I have just installed Ubuntu 14.04 next to my Windows 10, but I cannot get grub shown so I can boot Ubuntu.

On Windows I've disabled fast boot, secure boot and set the boot order so that the Windows Boot Loader is only above LAN-booting. 

I've booted a live session from usb to run boot-repair a few times. 

This is the first result: [http://paste.ubuntu.com/13150199/](http://paste.ubuntu.com/13150199/)
And second result: [http://paste.ubuntu.com/13151334/](http://paste.ubuntu.com/13151334/)

I've tried the suggested "[COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\u**[/COLOR][COLOR=#000000]buntu[/COLOR][COLOR=#BB6622]**\s**[/COLOR][COLOR=#000000]himx64.efi", and it says that the operation was succesful - but still no grub on restart. 

I've tried to mount sda7 and /dev, /sys and /proc, from a live session to un-hide grub, check efibootmgr and run 'sudo update-grub'. Which had a "[/COLOR][COLOR=#000000]Adding boot menu entry [/COLOR][COLOR=#AA22FF]**for **[/COLOR][COLOR=#000000]EFI firmware configuration" line - but still no grub on restart. 

**EDIT:** Grub does show but only for a split-second. I saw a glimse of a few lines that said "Failed ... " [/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR]```
[COLOR=#000000][FONT=Segoe UI]root@ubuntu:/# cat etc/default/grub[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]# If you change this file, run 'update-grub' afterwards to update[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]# /boot/grub/grub.cfg.[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]# For full documentation of the options in this file, see:[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]#   info -f grub -n 'Simple configuration'[/FONT][/COLOR]

[COLOR=#000000][FONT=Segoe UI]GRUB_DEFAULT="0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]#GRUB_HIDDEN_TIMEOUT=10[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]#GRUB_HIDDEN_TIMEOUT_QUIET=false[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]GRUB_TIMEOUT=10[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]GRUB_CMDLINE_LINUX=""[/FONT][/COLOR]

[COLOR=#000000][FONT=Segoe UI]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]# This works with Linux (no patch required) and with any kernel that obtains[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/FONT][/COLOR]

[COLOR=#000000][FONT=Segoe UI]# Uncomment to disable graphical terminal (grub-pc only)[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]#GRUB_TERMINAL=console[/FONT][/COLOR]

[COLOR=#000000][FONT=Segoe UI]# The resolution used on graphical terminal[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]# note that you can use only modes which your graphic card supports via VBE[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]# you can see them in real GRUB with the command `vbeinfo'[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]#GRUB_GFXMODE=640x480[/FONT][/COLOR]

[COLOR=#000000][FONT=Segoe UI]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]#GRUB_DISABLE_LINUX_UUID=true[/FONT][/COLOR]

[COLOR=#000000][FONT=Segoe UI]# Uncomment to disable generation of recovery mode menu entries[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]#GRUB_DISABLE_RECOVERY="true"[/FONT][/COLOR]

[COLOR=#000000][FONT=Segoe UI]# Uncomment to get a beep at grub start[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]#GRUB_INIT_TUNE="480 440 1"[/FONT][/COLOR][COLOR=#000000]
[/COLOR]
```[COLOR=#000000]

[/COLOR]```
[COLOR=#000000][FONT=Segoe UI]root@ubuntu:/# sudo update-grub[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]sudo: unable to resolve host ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Generating grub configuration file ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Found linux image: /boot/vmlinuz-3.19.0-32-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Found initrd image: /boot/initrd.img-3.19.0-32-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Found linux image: /boot/vmlinuz-3.19.0-25-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Found initrd image: /boot/initrd.img-3.19.0-25-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Adding boot menu entry for EFI firmware configuration[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]done[/FONT][/COLOR]

```[COLOR=#000000]

[/COLOR]```
[COLOR=#000000][FONT=Segoe UI]root@ubuntu:/# efibootmgr[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]BootCurrent: 0010[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Timeout: 2 seconds[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]BootOrder: 0010,000B,000A,000E,000D,000F,0012,000C,0011[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0000  Startup Interrupt Menu[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0001  Setup[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0002  Boot Menu[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0003  Diagnostic Splash Screen[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0004  Lenovo Diagnostics[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0005* ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot000A* USB CD[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot000B* USB FDD[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot000C* ATAPI CD0[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot000D* ATA HDD0[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot000E* ATA HDD1[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot000F* ATA HDD2[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0010* USB HDD[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0011* PCI LAN[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0012* Windows Boot Manager[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0013  ME Configuration Menu[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0014  Rescue and Recovery[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0015* IDER BOOT CDROM[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Boot0016* IDER BOOT Floppy[/FONT][/COLOR][COLOR=#000000]
[/COLOR]
```

[COLOR=#000000]I'm not sure how this "boot flag" thing works. A screenshot from gparted list sda2 as /boot. 

[/COLOR][ATTACH=CONFIG]265412[/ATTACH]

[COLOR=#000000]At this point I don't know how to proceed, any inputs or good ideas? 
[/COLOR]

---

### Post by oldfred on 2015-11-08
It says Lenovo, what model? And it shows dual video which may be another issue. You may need boot parameters for Intel or nVidia depending on which video chip is is actually using to boot with.

You show grub also installed to MBR, best not to have done that, but it should never be used, so no matter. But do not try to boot in BIOS/CSM/Legacy mode only UEFI boot mode.

With UEFI boot flag is just the way gparted indicates the ESP - efi system partition. It really is a very long GUID and just a short cut to assign the correct GUID for the ESP.
The boot flag with UEFI/gpt is not the same as a boot flag with BIOS and MBR partitioning. With MBR boot flag is the Windows bootable partition. Grub does not use boot flag, but Lilo & Syslinux boot loaders also use boot flag.

Your efibootmgr shows ubuntu as first boot entry. If you make Windows first then it may boot into Windows and the BCD entry to reboot UEFI (one time) may work to boot Ubuntu. You can try with the one time boot key. Not sure with Lenovo what key that is, but many systems use f10 or f12. But my Asus motherboard is f8.

Many systems have now modified UEFI to use description as part of boot. And only valid description is "Windows". That is specifically not allowed in UEFI standard, but perhaps some major operating system vendor is suggesting this, since just about every vendor now seems to have implemented it.

There are multiple work arounds, the BCDedit is one. UEFI also has a fallback or default boot entry for a device and that is also how external devices are booted. The entry is /EFI/Boot/bootx64.efi. So one work around is to copy shimx64.efi and make it bootx64.efi. You may have to add a hard drive entry into UEFI with efibootmgr, but some UEFI auto create it. Details in link in my signature below.

       T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

### Post by haffer on 2015-11-08
Hi Olfred, thanks for the reply. 

I actually managed to solve my issue before you posted - using a method from one of your threads !! ([http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295))

I did this: 

> [COLOR=#000000]A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot[/COLOR]

[COLOR=#000000]Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi Then boot harddrive entry in UEFI menu.[/COLOR]
[COLOR=#000000]Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)[/COLOR]

[COLOR=#000000]From live installer booted in UEFI mode, mount the efi partition on hard drive, lines with # are comments only: Mount ESP - efi system partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.[/COLOR]
[COLOR=#000000]# if your ESP is not sda1 change this to correct partition[/COLOR]
[COLOR=#000000]sudo mount /dev/sda1 /mnt[/COLOR]
[COLOR=#000000]only if /EFI/Boot not already existing, run the mkdir command,[/COLOR]
[COLOR=#000000]sudo mkdir /mnt/EFI/Boot[/COLOR]
[COLOR=#000000]sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot[/COLOR]
[COLOR=#000000]# If new folder created, the bootx64.efi will not exist, skip backup command[/COLOR]
[COLOR=#000000]sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup[/COLOR]
[COLOR=#000000]# make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.[/COLOR]
[COLOR=#000000]sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi[/COLOR]
[COLOR=#000000]# You may need new hard drive entry:[/COLOR]
[COLOR=#000000]sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"[/COLOR]
[COLOR=#000000]# confirm entries:[/COLOR]
[COLOR=#000000]sudo efibootmgr -v[/COLOR]

And now grub appears and I can boot whatever OS i desire :D . Thanks for the help!

---

### Post by oldfred on 2015-11-08
Glad that worked. :)

---

