---
title: "EasyBCD not working... dual boot of Win8 and ubuntu 12.04"
date: 2013-06-26
forum: Installation &amp; Upgrades
---

### Post by feardotcom on 2013-06-26
So i installed ubuntu on my new laptop from Dell (i know, that was my first mistake.) I followed a guide saying to install manually and set partitions up manually. Everything installed fine. I could get into windows 8 and linux but i had to to hit f12 for boot manager. Well, the guide i had went into detail about using EasyBCD to have windows add an entry for dual booting. First i would like to say that i think this program is a huge piece of crap. Every time i open this program it changes my entries around. I crashed the BCD and i had to order a recovery usb drive from dell. It's crashed it 3 times so far. All i would like is to have a menu that lets me choose between the OS's without having to frantically hit the F12 button repeatedly for 5 seconds after turning the power on. I've searched and searched and i cant find anything except for stuff that leads back to easybcd. The bios in this laptop are very limited. If i turn UEFI off then it wont even boot into anything. All i can do is go into bios. Does anyone have any ideas on what the heck is going wrong with easybcd? It's so screwed up, if i add an entry for ubuntu, it adds a second entry for windows 8 and says the path to ubuntu is C:\ and then if i delete that and go back to new entry it will put it something completely different.

---

### Post by Mark Phelps on 2013-06-26
Presuming that Win8 was preinstalled in UEFI mode, I'm guessing that you installed Ubuntu in BIOS mode -- which is why you have to use the boot manager every time?  I believe they BOTH have to use the same mode -- and I don't know the details of installing Ubuntu in EFI mode.

Our resident Expert on this (oldfred) is the person who can advise you with specifics on this -- and EasyBCD is probably NOT the right answer.

---

### Post by grahammechanical on 2013-06-26
I heard that EasyBCD did not work with Windows 8. But this shows that things have improved. So, I ask are you using that latest EasyBCD?

[https://neosmart.net/blog/2012/announcing-easybcd-2-2-windows-8-dual-booting-and-more/](https://neosmart.net/blog/2012/announcing-easybcd-2-2-windows-8-dual-booting-and-more/)

Regards.

---

### Post by oldfred on 2013-06-26
Best to see details. Some here that dual boot Windows 7 use EasyBCD, but it does compromise grub booting. With UEFI, it do not see much advantage of EasyBCD as the efi partition holds all the boot loaders and grub easily chainloads back to the Windows efi boot files. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by M4570D0N on 2013-06-26
EasyBCD has some functionality that still works, but mainly in Legacy mode (BIOS), and will most likely break your setup. In a BIOS setup on an MBR partition scheme, you had the boot manager ([FONT=courier new]bootmgr.exe[/FONT]) which would present the menu entries of the OS you want to install/run. The entries were contained in the Boot Configuration Data (BCD) and for Windows, the boot manager would also then invoke the bootloader ([FONT=courier new]winload.exe[/FONT]) to load the operating system kernel ([FONT=courier new]ntoskrnl.exe[/FONT]) and the boot-class device drivers. A UEFI setup typically uses a GUID Partition Table (GPT) but also supports MBR and does not on a boot sector. The boot configuration is controlled by a set of global NVRAM variables that indicate the paths to the loaders. Here, the relevant files for Windows would be [FONT=courier new]\EFI\Boot\bootx64.efi[/FONT] (bootloader), [FONT=courier new]\EFI\Microsoft\Boot\bootmgfw.efi[/FONT] (firmware boot manager/ UEFI boot manager) [FONT=courier new]C:\windows\system32\winload.efi[/FONT] (Windows boot loader), and [FONT=courier new] \EFI\Microsoft\Boot\bootmgr.efi[/FONT] (Windows boot manager). Additionally, if you wanted to edit the boot options in EFI, you could mount the EFI partition by opening up a command prompt and typing "[FONT=courier new]mountvol Z: /s[/FONT]"  to view and edit the options. This is similar to editing the BCD in a BIOS setup but this is command line only. This can also be done on Linux with efibootmgr and boot-repair. If I recall correctly, the ESP (EFI system partition) is usually labeled "[FONT=courier new]SYSTEM_DRV[/FONT]" in gparted or in the results log after running boot-repair. I seem to have had the most success/luck though with [rEFInd]("http://sourceforge.net/projects/refind/").

Here's a pdf of a powerpoint presentation from uefi.org by Microsoft's Kernel Platform Architecture Team that may be of some use int understanding a bit more about how the whole UEFI thing works:
[www.uefi.org/events/UEFI-Plugfest-WindowsBootEnvironment.pdf&#8206;]("http://www.uefi.org/events/UEFI-Plugfest-WindowsBootEnvironment.pdf&#8206;")

Also, for some more info on accessing the EFI partition from Windows, check out the Windows section on the install page for rEFInd:
[http://www.rodsbooks.com/refind/installing.html#windows](http://www.rodsbooks.com/refind/installing.html#windows)

---

