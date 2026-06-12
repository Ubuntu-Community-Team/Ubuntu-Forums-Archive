---
title: "Ubuntu 14.04 not booting after install alongside preinstalled Windows 8 UEFI"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by frk3 on 2014-04-24
I have a Toshiba l50-a-1d6 (i7 4700mq, Intel HD graphics 4600 + Nvidia gt740m) with Windows 8 UEFI preinstalled.

I installed Ubuntu 14.04 from a USB stick alongside Windows following the official documentation + this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
The problem is that i don't see GRUB2 at boot and Windows starts immediately.
So i ran boot-repair from live USB following this ([http://askubuntu.com/questions/449818/boot-repair-ppa-404-error-on-ubuntu-14-04](http://askubuntu.com/questions/449818/boot-repair-ppa-404-error-on-ubuntu-14-04)) cause there isn't boot-repair for 14.04 version, but it changed nothing.

Here's the boot info: [http://paste.ubuntu.com/7301085/](http://paste.ubuntu.com/7301085/)

---

### Post by oldfred on 2014-04-24
While it shows one or two strange errors I have seen those with other working installs. Not sure if just extranous entries or what.

Install looks ok.
But Ubuntu does not auto reset to be first in boot order in UEFI. Although Windows does on repair or update.
So can you go into UEFI and change boot order to make ubuntu entry first?

Some systems have hardware like hard drive, USB drive or DVD as one boot order list and UEFI entries like ubuntu & Windows as another list. Others just have one list.

Since Toshiba may be similar UEFI even if different model?
  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

---

### Post by frk3 on 2014-04-25
> **oldfred said:**
> Install looks ok.
But Ubuntu does not auto reset to be first in boot order in UEFI. Although Windows does on repair or update.
So can you go into UEFI and change boot order to make ubuntu entry first?

Some systems have hardware like hard drive, USB drive or DVD as one boot order list and UEFI entries like ubuntu & Windows as another list. Others just have one list.


In bios boot order i can select only USB, HDD, DVD or LAN.
After some research i found this: [http://www.rodsbooks.com/linux-uefi/#troubleshooting](http://www.rodsbooks.com/linux-uefi/#troubleshooting)
From there: "[B]Hijack the Windows boot loader&#8212;Some buggy EFIs boot only the Windows boot loader, which is called EFI/Microsoft/Boot/bootmgfw.efi on the ESP. Thus, you may need to rename this boot loader to something else (I recommend moving it down one level, to EFI/Microsoft/bootmgfw.efi) and putting a copy of your preferred boot loader in its place.[FONT=Verdana]"

[/FONT][/B][FONT=Verdana]As we can see from the pastebin i have [/FONT]** EFI/Microsoft/Boot/bootmgfw.efi entry**, so can i use efibootmgr command from live usb to change boot order (but I don't know how to use it without making stupid things)?
I'm seeing this "guide":[http://www.rodsbooks.com/efi-bootloaders/installation.html](http://www.rodsbooks.com/efi-bootloaders/installation.html), but not sure what i really need to do.
Or is there another tool for managing UEFI boot order?

---

### Post by oldfred on 2014-04-25
Others with Toshiba have not had to do the rename.

This user found two boot order settings in UEFI, one for hardware and another for UEFI devices.
       
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)

      
 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)


  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

Many of the issues have been fixed in 14.04, so older fixes may not apply.
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by ubfan1 on 2014-04-25
Windows will never give up putting itself into first place, so I just habitually use the efi-boot menu (F12 on my Toshiba Satellite s855) to select ubuntu.

---

### Post by frk3 on 2014-04-25
> **ubfan1 said:**
> Windows will never give up putting itself into first place, so I just habitually use the efi-boot menu (F12 on my Toshiba Satellite s855) to select ubuntu.

The problem is that if i press F12 at startup i can only select USB, HHD, DVD or LAN. I don't know if there's some hidden efi options :confused:

> **oldfred said:**
> 
 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're  deleting the right one, and then you use the combination of "-b ####"  (to specify the entry) and "-B" (to delete it).

This is the output of sudo efibootmgr -v (i see only Windows Boot Manager:confused:);
```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0000,2003,2001,2002
Boot0000* Windows Boot Manager    HD(2,200800,32000,778e626f-6364-11e3-9faa-0c54a54d3e5a)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* UEFI: Network Card     ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(2025642eb42e,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: Network Card     ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(2025642eb42e,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* UEFI:  USB Flash Memory1.00    ACPI(a0341d0,0)PCI(14,0)USB(4,0)HD(1,3f,3c53c1,000b6da4)..BO
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

```

I mounted the efi partition from the live USB so I see this files;
```
ubuntu@ubuntu:/boot/efi/EFI$ ls
Boot  Microsoft  Toshiba  ubuntu
ubuntu@ubuntu:/boot/efi/EFI$ ls Boot
bootx64.efi
ubuntu@ubuntu:/boot/efi/EFI$ ls Microsoft/Boot/
BCD           BOOTSTAT.DAT  en-US  hu-HU        nb-NO      ro-RO       tr-TR
BCD.LOG       boot.stl      es-ES  it-IT        nl-NL      ru-RU       uk-UA
BCD.LOG1      cs-CZ         et-EE  ja-JP        pl-PL      sk-SK       zh-CN
BCD.LOG2      da-DK         fi-FI  ko-KR        pt-BR      sl-SI       zh-HK
bg-BG         de-DE         Fonts  lt-LT        pt-PT      sr-Latn-CS  zh-TW
bootmgfw.efi  el-GR         fr-FR  lv-LV        qps-ploc   sr-Latn-RS
bootmgr.efi   en-GB         hr-HR  memtest.efi  Resources  sv-SE
ubuntu@ubuntu:/boot/efi/EFI$ ls Toshiba/Boot/
BCD           boot.stl  en-US  hr-HR  lv-LV        pt-PT      sl-SI       zh-CN
BCD.LOG       cs-CZ     es-ES  hu-HU  memtest.efi  qps-ploc   sr-Latn-CS  zh-HK
bg-BG         da-DK     et-EE  it-IT  nb-NO        Resources  sr-Latn-RS  zh-TW
bootmgfw.efi  de-DE     fi-FI  ja-JP  nl-NL        ro-RO      sv-SE
bootmgr.efi   el-GR     Fonts  ko-KR  pl-PL        ru-RU      tr-TR
BOOTSTAT.DAT  en-GB     fr-FR  lt-LT  pt-BR        sk-SK      uk-UA
ubuntu@ubuntu:/boot/efi/EFI$ ls ubuntu/
grub.cfg  grubx64.efi  MokManager.efi  shimx64.efi

```


I read (here [http://www.rodsbooks.com/efi-bootloaders/installation.html](http://www.rodsbooks.com/efi-bootloaders/installation.html)) that EFI/Microsoft/BOOT/bootmgfw.efi is the default file, but which is the right file to boot into grub?
I have to register the right bootloader? In the link he suggests some possibilities...

---

### Post by oldfred on 2014-04-25
I have seen several solutions.
One is Boot-Repair 'buggy' UEFI fix which renames bootmgfw.efi and makes that file shim. Some have done the same manually. But then you can only boot Windows from grub menu with the renamed file. 
Some have renamed bootx64.efi to be shim. Not sure what boot entry that becomes?
Some have added an entry to BCD so Windows is chainloading back to shim. But Windows seems to shutdown and reboot that entry so it seems like it is doing a lot.
Some find rEFInd works to resolve the issues.

       Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

      
  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)


 Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)

      
 Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)


 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by frk3 on 2014-04-28
> **oldfred said:**
> 
 Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)


This worked great! Now I have dual boot working.
From live usb i mounted the efi partition and then i followed post #6. Only a matter of copying the right loader files in the right place (/EFI/Microsoft/Boot and also in /EFI/Boot for no worries).

INFO: I also tried to create a new loader for grub with the command "efibootmgr" and  put this before windows loader in boot order, but didn't worked.

Thanks a lot oldfred.
Can we advise boot repair team about this issue with the windows loader manager beeing default and the only bootable (if i'm not wrong)?

---

### Post by oldfred on 2014-04-28
Glad that worked.

Boot-Repairs fix has always been the rename of the Windows efi file and make shim have Windows file name so UEFI thinks it boots Windows. 

But then you only can boot Windows from grub menu and Windows updates will overwrite the shim file as it has the Windows name and you have to rename again.
Manually doing it helps you understand changes, so when Windows updates you know what to change again.

Not sure if different systems also have different solutions. It seems the UEFI 'standard' is not much of a standard as every vendor seems to modify it.

---

### Post by ubfan1 on 2014-04-28
Now that you presumably have an ubuntu nvram entry to boot, the efi boot menu (F12) when HDD is selected should pop up a second window giving you the Windows or Ubuntu choice.

---

### Post by leo0226 on 2014-09-07
I follow the steps to change the boot order with the efibootmgr, the problem is that in the initial boot order Ubuntu was at the beggining of the list. The windows boot manager was in the second place. I dont know why Ubuntu cant boot. My pc is a toshiba satellite p55-a5105sl.

---

### Post by oldfred on 2014-09-08
@leo02226
This is now a solved thread, so the solutions worked for the original poster.
If you cannot use the same solutions, may be best to start your own thread, so we can see what issues are unique.

Some more recent info on renaming files which seems to be one of the main solutions now.
 Manually copy efi files to efi partition on flash drive for booting. Toshiba Satellite S855-5378  by ubfan1
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)

      
 [http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

