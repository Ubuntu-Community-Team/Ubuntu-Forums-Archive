---
title: "Dual boot Ubuntu 16.04 with preinstalled Windows 10 Dell G5 5587"
date: 2019-06-15
forum: Installation &amp; Upgrades
---

### Post by arshovon on 2019-06-15
I am trying to install+dual boot Ubuntu 16.04(LTS) with pre installed Windows 10(home) in my Dell G5 5587. Windows is installed in SSD. I have 1TB HDD alongside the SSD.


I did the following:


- Freed 100 GB from SSD and created 100 GB unallocated space.
- Turned off Windows 10 Fast boot.
- Turned off Secure boot feature from BIOS. 
- Changed Secure boot mode to audit mode in BIOS. 


*msinfo32* is showing:

```

    BIOS Mode            UEFI
    Secure Boot State    Off
```


The BIOS is showing UEFI on, Secure Boot off, PTT on.


**Approach 1 (MBR+UEFI/Legacy)**


I burned Ubuntu using Rufus(MBR+UEFI/Legacy) to a pendrive. I got the pendrive in the one time boot menu(F12). When I try to install Ubuntu it showed the following warning:


> "This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.


If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here.")


[IMG]https://i.stack.imgur.com/wRpsI.jpg[/IMG]

As I do not want to risk losing Windows, I aborted installing Ubuntu.


**Approach 2 (GPT+UEFI)**


If I burn the Ubuntu OS using Rufus(GPT+UEFI), I do not find the pendrive in one time boot menu(F12). 


**Question**


How to properly install dual boot Ubuntu 16.04 LTS with pre installed Windows 10 in Dell G5 5587?

---

### Post by yancek on 2019-06-15
Ubuntu has its own site on dual booting with windows 10 at the link below.  While booted into the Ubuntu installer, open a terminal and run the command:

```
sudo parted -ll
```

that's a lower case Letter L in the command.  It should show a UEFI partition if you are using UEFI.  Your installer seems to see it as a Legacy install.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-06-15
You may do better with 18.04 as Dell released drivers for new systems and eventually they get included in kernel & distributions.

Most Dell have needed UEFI update from Dell (even if new) and SSD firmware updates.
Drives need to be changed to AHCI from RAID or Intel SRT. If still using Windows add AHCI driver to Windows first.
If nVidia you need nomodeset until you install nVidia driver from Ubuntu repository. I think newest 19.04 now includes adding a nVidia driver if you check add proprietary during install. Otherwise first boot also use nomodeset.

       Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)

Just about all models of Dell need same fixes to boot, bigger difference if Intel or AMD based.
       
 Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)
Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929)

---

