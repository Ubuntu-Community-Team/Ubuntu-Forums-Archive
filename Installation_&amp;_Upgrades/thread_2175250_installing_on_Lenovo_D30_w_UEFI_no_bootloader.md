---
title: "installing on Lenovo D30 w/ UEFI: no bootloader?"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by Doug_Kelley on 2013-09-18
Hi everybody--
I've got a shiny new Lenovo D30 and am working to install Ubuntu 12.04. (New to Ubuntu but knowledgeable at the unix command line.) The machine came pre-loaded with Windows 7, and Wubi worked fine. I removed Windows to install Ubuntu as the sole operating system using a 12.04 64bit LiveDVD (made from the .iso and verified). Alas, after much tinkering the problem persists: "Error 1962: No operating system found. Press any key to repeat boot sequence." 

I've been working from [these great instructions. ]("https://help.ubuntu.com/community/UEFI")In the BIOS, I disabled Quick Boot and set "UEFI Boot Mode" to UEFI (not automatic). I didn't find mention of Intel Smart Response Technology, nor FastStartup (that's Windows 8 only, right?). I've tried setting up partitions manually, or allowing the installer to take the whole drive. Either way, the installer finishes successfully, but on reboot the machine can't find any operating system. 

I [ran Boot Repair]("http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/") and got [these results]("http://paste.ubuntu.com/6123832/"). They say there's no boot loader in the MBR--ack! 

Also, once installation has completed successfully, as the machine is shutting down I get a funny message about display driver trouble that usually locks the machine and requires manual power cycling. Not sure if it's related. 

Thanks in advance for any help you can give! This is turning into a real bear.

--Doug

---

### Post by oldfred on 2013-09-18
If you had wubi before, then your Windows was in BIOS/MBR mode. Wubi does not work with gpt partitioning that UEFI has to have.

Lets see details:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Doug_Kelley on 2013-09-18
oldfred, thanks for responding. Here's the [Boot-Info report]("http://paste.ubuntu.com/6123832/").

---

### Post by oldfred on 2013-09-18
It looks like you have a standard UEFI install.

You do show the Windows boot folder with its boot files in the efi partition. 

Extract of your UEFI choices as show on line 691:
 BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0000,0004,0001,0002,0003
Boot0000* ubuntu	HD(1,800,2f000,2d49c916-e4d6-4ef5-bd76-dca808584c9c)File(EFIubuntugrubx64.efi)
Boot0001* HL-DT-STDVD-RAM GHA2N	BIOS(3,0,00)AMBO
Boot0002* ST1000DM003-1CH162	BIOS(2,0,00)AMBO
Boot0003* IBA GE Slot 00C8 v1372	BIOS(6,0,00)AMBO
Boot0004* UEFI: HL-DT-STDVD-RAM GHA2N	ACPI(a0341d0,0)PCI(1f,2)03120a000000ffff0000CD-ROM(1,57e49,1100)AMBO



Have you turned off secure boot? It looks like it should boot with it on.
It looks like you have installed Ubuntu in secure boot mode as grub shows that as current boot with signed kernel, but all previous versions are unsigned or just UEFI without secure boot.
If you booted Boot-Repair with secure boot on it would have updated to signed versions.

A few UEFI system have modified UEFI to only boot the Windows efi file. That is not UEFI standard and if your system it that way you should complain to vendor. And/or update UEFI/BIOS in case that has been fixed. 
 If you can only boot Windows, Boot-Repair has a work around to rename the Windows efi file to actually be the grub shim file that has the Microsoft signing key and will boot grub instead.

       Rename will occure if Boot-Repair sees Windows kernel issues, but may not always be required. 
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]?
Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by Doug_Kelley on 2013-09-19
oldfred, thanks for the thoughts. Some responses:

> You do show the Windows boot folder with its boot files in the efi partition.
This surprises me. I've repartitioned and formatted numerous times since Windows 7 was on the drive--Windows is long gone. Does Ubuntu re-install a Windows boot folder? 

> Have you turned off secure boot? It looks like it should boot with it on.
Just now I found a buried BIOS setting called "TGC Security Feature" which I hadn't found before. I can changed it from "Inactive" to "Active", which caused a message "Secure boot installed" to appear after the Lenovo splash screen. But this change didn't cause the machine to boot properly.

> Rename will occure if Boot-Repair sees Windows kernel issues, but may not always be required. 
I booted from DVD and ran Boot-Repair, choosing Advanced Options > Main options > Backup and rename Windows EFI files (solves the [hard-coded-EFI] error). Still no boot. Here's the [Boot-Info report]("http://paste.ubuntu.com/6128163/"). 

> Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair -->  Advanced Options --> "GRUB options" tab --> tick "SecureBoot"  --> Apply.
I booted from DVD again and did this. Still no boot. Here's the [Boot-Info report]("http://paste.ubuntu.com/6128200/"). 

Then I booted from DVD again and enabled both options in Boot-Repair (backing up the Windows EFI files and enabling SecureBoot). Here's the [Boot-Info report]("http://paste.ubuntu.com/6128248/"). I also manually mounted the EFI partition and verified that /EFI/Microsoft/Boot/shimx64.efi didn't exist, but bootmgfw.efi did (as well as bootmgfw.efi.grb). Still no boot.

So I'm stumped again. Any ideas about what to try next? Thanks in advance!

---

### Post by oldfred on 2013-09-19
From some other threads with Lenovo. May have clues on fixes?

Someone mentioned this as an issue with his Lenovo.
 Lenovo Active Protection System&#8482; &#8211; for hard drive

Someone else mentioned this, but it sounds like your does work?

 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

Other Lenovo

 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.
Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED - other issues
[http://ubuntuforums.org/showthread.php?t=2170099](http://ubuntuforums.org/showthread.php?t=2170099)

---

### Post by Doug_Kelley on 2013-09-19
oldfred, thanks--I'll read about these Lenovo-specific issues. Meanwhile, a thought: I could abandon UEFI and GPT altogether in favor of BIOS and MBR. Would that simplify things? Since I'm not dual-booting and I don't need a lot of partitions, I can't think of any big drawbacks.

---

### Post by oldfred on 2013-09-19
You can stay with gpt, I have a 6 year old system and converted one drive to gpt and use it to boot from. Then new SSD is gpt also now. You have to add a tiny 1MB unformatted partition with bios_grub flag to get grub to install correctly with BIOS.

You can add bios_grub partition anywhere on drive with gparted, and use Boot-Repair to convert a UEFI install to BIOS by uninstalling grub-efi and installing grub-pc.  

I suggest leaving efi partition on drive as it is not large and later on they may fix issues and you then could convert back to UEFI.

Only Windows requires UEFI to boot from gpt drives. Both Windows and Ubuntu only boot from MBR drives with BIOS. But Ubuntu boots with either UEFI or BIOS from gpt if correct efi or bios_grub partitions exist.

---

### Post by Doug_Kelley on 2013-09-24
Good news: the machine is running. I went back to the BIOS, verified that SecureBoot and Quick Boot were disabled, set the boot mode to Legacy (not UEFI nor auto), and set "CSM support" to enabled (not auto). Then I booted from the Ubuntu 12.04 DVD (seeing the [purple screen indicating a legacy boot]("https://help.ubuntu.com/community/UEFI") as it came up). With gparted I created a new msdos (not GPT) partition table on the hard drive. Then I installed Ubuntu with default settings and all was well. 

Maybe someday I'll have time and motive to wrangle with UEFI. But not today, and not tomorrow! oldfred, thanks again for your time and know-how.

---

### Post by oldfred on 2013-09-24
Whatever works. 

UEFI is new and both vendors, Windows, and Linux are working to get all the issues resolved. Some systems work easier than others for whatever reason. But UEFI has CSM or compatibility for old BIOS and MBR to work with older systems and then can be used as an older install. Later on that may be an issue only as new hardware is not as well supported in BIOS mode.

---

