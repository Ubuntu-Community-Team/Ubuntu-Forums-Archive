---
title: "Tried to add entry to GRUB, now it's messed up."
date: 2021-05-14
forum: Installation &amp; Upgrades
---

### Post by timbalisto on 2021-05-14
I have two SSDs, Windows 10 installed on the larger of the two. I just installed Kubuntu on the smaller SSD. When I rebooted from the installation, Win 10 was not an option in GRUB.

I booted into Kubuntu and did sudo os-prober, which returned nothing. Rebooted, there are more disk entries in my BIOS, some of them look identical. Windows still wasn't in GRUB. I booted into Kubuntu and ran os-prober again. Rebooted and GRUB is gone from the primary boot entry, boots directly into Kubuntu.

Some of the BIOS boot entries go to GRUB, but none of its entries work. Every BIOS boot entry goes to Kubuntu or a non-working GRUB, even the one Windows entry.

I have usb installation media for Kubuntu and Windows 10.

Please help, I'm desperate to get the Windows disk bootable.

---

### Post by ubfan1 on 2021-05-15
First determine how Windows 10 is installed, legacy or UEFI.  Although machines from the manufacturer with Windows have been UEFI for about 10 years, a Win 7 upgrade to Win8 then Win 10 may very well be in legacy mode.  If Windows is in UEFI mode, its disk will have gpt partitioning, if in legacy mode, the partitioning will be msdos.  At power on, bring up the UEFI menu with some function key to give you a boot choice of device or OS, select Windows, which bypasses grub completely.  More details about your partitions would also help decide what fix is needed.  Likely, Ubuntu got installed in the other mode from Windows.  How the install media boots is how the install is done, and UEFI Settings/BIOS controls how the install media boots.

---

### Post by timbalisto on 2021-05-15
The PC is UEFI, but I used YUMI usb Legacy mode to install both OSs, so I think both were installed as Legacy. All boot choices boot Kubuntu or a non-functional GRUB.

I can reinstall both OSs, but I'd rather not have to.

---

### Post by tea for one on 2021-05-15
> **timbalisto said:**
> The PC is UEFI, but I used YUMI usb Legacy mode to install both OSs, so I think both were installed as Legacy. 

Windows 10 in Legacy mode is very unusual.

Possibly, for a quick fix, power off and physically remove the Kubuntu ssd.

Does the PC find the Windows boot manager?

---

### Post by timbalisto on 2021-05-15
I disconnected the Kubuntu SSD. When I choose the Windows SSD in the BIOS there's a black screen with a white text cursor moving back and forth for a few seconds, then it puts me back into the BIOS.

---

### Post by tea for one on 2021-05-15
You mentioned that you had Windows 10 installation media and that access to Windows is your immediate priority.

Therefore, repair Windows 10 with your Windows disk and then we'll figure out Kubuntu later.

After you have repaired Windows, it is essential to know if it is installed in UEFI mode.

Check via System Information > System Summary > BIOS mode > UEFI (or BIOS) - hopefully UEFI

---

### Post by oldfred on 2021-05-15
A default install, will install grub to first drive, so it probably put grub boot loader in Windows SSD.
And if Windows BIOS/MBR then you can only boot Windows from grub.
And Windows 10 in BIOS mode is not very friendly with dual boot. Since two drives you can make it functional.
Issue is Windows 10 will turn fast start up back on with updates. And then grub cannot boot Windows. If you keep the Windows boot loader on Windows drive, you should be able to directly boot Windows, turn fast start up off & then change default boot back to grub/Ubuntu.
UEFI in effect is like multiple MBRs as multiple boot loaders can be in one ESP - efi system partition, but often better to have ESP on each bootable drive, in case of issues on boot drive.

Windows in BIOS mode requires MBR partitioning which started in the 1980's. It has been replaced with gpt which Windows requires with UEFI booting. Ubuntu can boot in UEFI or BIOS mode from either gpt or MBR. But with Ubuntu better to just always use gpt, now.
Since UEFI system, better to use gpt partitioning. If you really want old BIOS/MBR configuration then at least use gpt on Ubuntu drive and add both bios_grub partition (1MB unformatted with bios_grub flag) for grub to install in BIOS mode and an ESP (FAT32 300 to 500MB with esp/boot flags) so Ubuntu install can easily be converted from BIOS to UEFI. Only real difference is version of grub.

You need to always have Windows repair/recovery drive and Ubuntu live installer to make repairs.
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10)

You have to use your Windows repair tools to reinstall a Windows boot loader to Windows drive.
But with BIOS can use Boot-Repair to install a Windows type BIOS boot loader (syslinux).
And then in Boot-Repair's advanced mode, should be able to choose Linux install and Linux drive (not partition) to install grub. Then in UEFI/BIOS choose Ubuntu drive as default boot.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by timbalisto on 2021-05-15
I tried to repair with the installation media, but it said Startup repair couldn't repair your PC. 

Some errors I came across when going through GRUB entries and reboots: 

Error: can'tfind cammand 'fwsetup'.

EFI stub: ERROR: exit-boot() failed!
EFI stub: ERROR efi_main() failed!

---

### Post by timbalisto on 2021-05-15
I don't have a preference for BIOS over UEFI, it's just what I was used to.

[Here is the pastebin link]("https://paste.ubuntu.com/p/GJXF25Sgjd/").

---

### Post by tea for one on 2021-05-15
[COLOR="#0000FF"]Lines 89 & 96[/COLOR] - Windows on sdb1 is not gpt 
[COLOR="#0000FF"]Line 232[/COLOR] - legacy-win no-win-efi 
[COLOR="#0000FF"]Line 88 & 94[/COLOR] - Kubuntu with gpt and UEFI

You have mixed mode installations, which is not advisable.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I suspect that the Windows repair failed due to Legacy Windows, although I'm not sure.

I think that you need to future-proof your system and, in your position, I would:-

Back up all my data
Install Windows in UEFI mode with gpt
Restore and check data
Isolate, de-activate, remove Windows disk

Install Kubuntu in UEFI mode with gpt
Restore and check data

Boot from UEFI boot order without worrying about grub.
Each OS on separate disks is ideal.

If you keep mixed mode installations, a grub update in the future will give you the same problem again
Grub updates are pretty important as they may fix security flaws.

---

### Post by oldfred on 2021-05-15
You have Ubuntu in UEFI boot mode with gpt partitioning on sda. 
But you also have a BIOS boot version of grub in MBR of sda and a bios_grub partition. Looks like you installed twice, once BIOS and once UEFI. But since fstab shows mount of ESP - efi system partition, it looks like current install is UEFI.
If you set UEFI to boot in UEFI mode, it should boot Ubuntu. And grub in gpt's protective MBR will never be used and should not be.

Windows is on MBR drive, so BIOS install.
Was sda default boot drive in UEFI/BIOS when you installed Windows? Windows in BIOS mode has a separate small boot partition, which will be on default UEFI/BIOS drive. Yours is missing as if it was installed on sda, and then install of Ubuntu overwrote it. Or now you are missing essential Windows boot files. Probably better to disconnect sda, and totally reinstall Windows in UEFI mode to sdb drive. 
If you really want BIOS Windows, you can move boot flag to sdb1 and boot Windows repair in BIOS mode. It does not absolutely have to have separate boot partition.

How you boot install media, both Ubuntu & Windows is then how it installs or repairs. With UEFI hardware best to always boot in UEFI mode from UEFI boot menu & then have UEFI set default boot of installed systems to UEFI.

---

### Post by timbalisto on 2021-05-15
Looks like I'm doing fresh installs, luckily, I have most of my files on an external HDD. I borrowed my neighbor's laptop to make a usb stick with YUMI. It's one of the few (in my short search) usb installers that can do Linux and Windows ISOs on the same stick, and can do EUFI.

Should I disconnect the SSD that's not currently in use when I do both EUFI installs to their own SSD?

Thanks for the help!

---

### Post by oldfred on 2021-05-15
Safest to disconnect other drive. Just be sure to boot all installers in UEFI boot mode.
Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Sometimes you have to re-add UEFI boot entry. when a drive is disconnected UEFI forgets boot entry.
Most UEFI seem to find Windows, but not Linux boot loaders. 
You can reinstall grub or use efibootmgr to just add/correct the UEFI boot entry for Ubuntu.

---

### Post by timbalisto on 2021-05-15
I did a fresh install of both systems while having the opposite SSD disconnected. I am able to boot into both, but Kubuntu has GRUB start up when I choose it in the EUFI boot menu. I thought if Kubuntu saw it was the only drive connected when it was installing, it wouldn't install GRUB. Everything's usable, just another hoop to jump through.

Thanks!

---

### Post by tea for one on 2021-05-16
Very wise to take the time to re-install in UEFI mode.

Ubuntu family members always install Grub but you can [COLOR="#0000FF"]hide[/COLOR] the menu if you wish.

However, unless your Windows drive is inaccessible, when you run **sudo update-grub**, grub will add the Windows Boot Manager.

Personally, I like to see the Grub menu because it allows you to easily boot alternative kernels or enter the UEFI set-up pages.

---

### Post by oldfred on 2021-05-16
Grub is the boot loader and is required.
You can change many settings in grub, but if you have run sudo update-grub to add Windows to grub menu, then it will normally show.
It also shows if shutdown is not normal, so you can use recovery mode to make repairs.
But with one install in menu, it should not normally show.

I have multiple installs, but normally boot into main working install. So I change menu to 3 seconds from default of 10, just to have enough time to get to menu if I want to go into a test install.

---

