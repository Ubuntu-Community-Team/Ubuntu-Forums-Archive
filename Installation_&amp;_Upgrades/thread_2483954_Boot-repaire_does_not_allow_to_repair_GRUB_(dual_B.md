---
title: "Boot-repaire does not allow to repair GRUB (dual Boot)"
date: 2023-02-13
forum: Installation &amp; Upgrades
---

### Post by rgodon on 2023-02-13
Hello to all.
I have a laptop in dual boot windows 10 / ubuntu 22.04. Following a Windows update the ubuntu boot disappeared. I tried several options found on forums to repair Grub, manually or using boot-repair. However nothing works, ubuntu is still there and I recovered the data with a live USB but the ubuntu boot does not appear either at boot time or in the BIOS boot menu. Here is the information provided by Boot-repaire.


[https://paste.ubuntu.com/p/FMDR476NFn/](https://paste.ubuntu.com/p/FMDR476NFn/)
[https://paste.ubuntu.com/p/ysKMjDbcjJ/](https://paste.ubuntu.com/p/ysKMjDbcjJ/)


I hope to have provided all the necessary information.
If someone has an idea of the problem it would be great.


Thanks in advance


Roland

---

### Post by grahammechanical on 2023-02-13
I have heard that an update to Microsoft Windows will re-activate Fast Startup which must be disabled if Ubuntu is to load. Another point to consider is the need to set the UEFI settings utility to boot from sda2. That is where the boot files for both Microsoft and Ubuntu are. 

I am a little bit troubled about Boot Repair saying that Windows is installed in the MBR  of sda. I think that should only apply is Windows is installed in legacy/CSM mode. I do not think any thing should be in the MBR when both Windows and Ubuntu are installed in UEFI mode. Which seems to be the case. Of course I may be wrong about this.

Regards

---

### Post by oldfred on 2023-02-13
You must have an old drive to have a Windows boot loader in MBR. Actually now gpt's protective MBR.
Windows only boots in UEFI boot mode from gpt partitioned drives.

You now show UEFI Secure Boot on and a bitlocker partition.
Did Windows do an update & restore UEFI settings & Windows settings to defaults?
Unless Ubuntu installs in Secure Boot mode it needs Secure boot off.

Check UEFI & Windows settings.

---

### Post by rgodon on 2023-02-13
Thank you very much to both of you for your interest in my request. 


I don't know exactly what windows did as an update (or repair) but it must have indeed made important changes because the bitlocker key was requested at boot time. This happens every time the partitions are modified (when creating the dual boot). 


It is possible that the windows installation is not completely conventional because the disk was provided to me empty by the windows support, following a failure of the first one and they "explained" me very badly how to reinstall windows on it. I then did a Ubuntu dualboot years later and everything worked fine before this "upgrade". I don't want to spend unnecessary energy to fix Windows that works well enough for its little use. Unless it allows me to get Ubuntu back without reinstalling everything of course! 


In the update history the last one is this one and corresponds to the day of the failure 


January 10, 2023 - KB5022282 (operating system builds 19042.2486, 19044.2486 and 19045.2486)


I don't know what you mean by windows settings but here is the version used 


Windows 10 Professional Edition
Version 22H2
Installed on 12/10/2020
Operating system build 19045.2486
Windows Feature Experience Pack 120.2212.4190.0


I am sincerely sorry it is in French I prefer not to translate to avoid the contresens.


Concerning UEFI settings again I hope this is the answer you are waiting for. 


UEFI - windows Boot manager
UEFI N/W 4 IPV4 Network - Realtek PCIe GBE Family Controller
UEFI N/W 6 IPV6 Network - Realtek PCIe GBE Family Controller


I don't know if this brings much information.


Do you think I have a chance to recover the ubuntu boot without reinstalling?

---

### Post by oldfred on 2023-02-13
Did you try turning UEFI Secure Boot off.
And Windows bitlocker and fast start up?
Sometimes UEFI update turns RAID drive setting back on, when you previously had changed to AHCI. Windows has to have AHCI drivers to work, but if previously installed it still should work.

Then try reinstalling grub. Be sure to always boot in UEFI boot mode, so repairs are always in UEFI mode.

---

### Post by rgodon on 2023-02-14
[COLOR=#000000][FONT=Arial]Hello, [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I tried to enable or disable the secure boot. Bitlocker is disabled and also fast start.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Nothing happened. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I did a reinstall of Ubuntu keeping the Home. This allowed Ubuntu to reappear in the boot menu. However this message is displayed:[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial][[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]0.188867] x86/cpu: VMX (outside TXT) disabled by BIOS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]0.188867] x86/cpu: SGX disabled by BIOS.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Gave up waiting for root file system device.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]common problems:[/FONT][/COLOR]

[LIST]
[*]Boot argos (cat /proc/cmdline)

[LIST]
[*]check rootdelay= (did the system wait long enough?)
[/LIST]
[/LIST]
[COLOR=#000000][FONT=Arial]- missing modules (cat /proc/modules; ls /dev)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ALERT! UUID=6dc1df43-fd86-438b-a151-db7b5082994d does not exist. Dropping the shell![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Enter &#8216;help&#8217; for a list of built-in commands.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](initramfs)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]In the BIOS I managed to enable VMX and SGX so the first two lines disappeared. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The problem "UUID does not exist dropping the shell" seems to be indeed due to a RAID and AHCI problem. However my bios does not allow to make this change according to my research. (HP Probook 450 G5). [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Windows mentions a BIOS update to allow it. I don't remember if the bios allowed it before my problem but an automatic return to an old version seems unlikely? Whereas it worked very well before. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks again for taking the time to help me.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by oldfred on 2023-02-14
VMX only required for Virtual memory installs
VMX stands for Virtual Machine Extensions and it is a virtualization technology.
Better memory isolation, but may want UEFI Secure boot off and SGX on.
SGX Intel® Software Guard Extensions (SGX) is a security technology Skylake or later Intel

Note: UEFI firmware update may reset some settings to defaults. You often have to redo some or all the changes you make. 
HP is only vendor that when Ubuntu installs & uses efibootmgr to change boot order, it does not work. You can only change boot order in UEFI settings menu (not boot menu).

You may need to reinstall grub as if older grub still there & trying to boot previous UUID.

Possibly similar issues:
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Zbook 15 NVRAM locked, install issues
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)

---

