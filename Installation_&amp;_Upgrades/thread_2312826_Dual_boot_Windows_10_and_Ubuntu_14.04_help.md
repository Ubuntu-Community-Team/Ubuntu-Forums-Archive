---
title: "Dual boot Windows 10 and Ubuntu 14.04 help"
date: 2016-02-07
forum: Installation &amp; Upgrades
---

### Post by Chris_Jakins on 2016-02-07
So I just tried to install Ubuntu after having Windows 10 already installed, but my computer will only boot into Windows unless I have the trial CD for Ubuntu in. Fast startup/Hibernate is disabled in my Windows options.

Not sure where to go from here.

---

### Post by grahammechanical on 2016-02-07
> but my computer will only boot into Windows unless I have the trial CD for Ubuntu in.

Have you actually installed Ubuntu? When installing Ubuntu did you go through an install procedure like this?

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> 
[LIST]
[*]if the other systems (Windows Vista/7/8, GNU/Linux...) of your  computer are installed in UEFI mode, then you must install Ubuntu in  UEFI mode too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]


If the machine came with either Windows 10 pre-installed or Windows 8.1 pre-installed & then upgraded to Windows 10, then Window most definitely installed in efi mode. And we need to run the Ubuntu live session in efi mode for Ubuntu to be installed in efi.

If we have Windows installed in efi mode and Ubuntu installed in BIOS/Legacy mode then it is possible that the machine will boot only into Windows and you will only be able to load Ubuntu if you load again a live session.

You can enter the UEFI boot system settings and change to BIOS/Legacy mode but then you will only be able to load Ubuntu and not Windows 10.

Regards.

---

### Post by Chris_Jakins on 2016-02-07
I should've been more clear.. Yes, I've installed Ubuntu. I went through the process of partitioning on the liveCD through gparted.

I wasn't aware that there was an option to choose Legacy or UEFI. Where can I check these settings and how would I change them?

EDIT: I just looked at the second link you sent me. Lol. I will go through this and post here if I have another question. Thank you!

---

### Post by Chris_Jakins on 2016-02-07
Ok, so that link suggested I disable CSM in the UEFI settings as that could potentially be an issue. That somehow changed my boot priority as before my comp would boot the CD on startup, but after disabling CSM it booted straight into Windows. 

So I went back into the UEFI settings and booted from the CD-rom, found out I was running 64-bit Ubuntu. I ran ' [COLOR=#333333][FONT=Ubuntu][ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode" ' in the terminal and it said installed in UEFI mode...

So I'm confirmed in UEFI mode (pretty sure for both OSs).[/FONT][/COLOR]

---

### Post by Dennis N on 2016-02-08
Is Windows listed first in the UEFI boot manager's menu boot order? If so, you won't get the grub menu. Change the order so Ubuntu on your hard drive is first, then reboot and you should get to the grub menu where you can select either Windows or Ubuntu.

---

### Post by Chris_Jakins on 2016-02-08
Actually, when I don't have any installation media plugged in, Ubuntu isn't listed on my boot priority. The only thing listed is 'Windows Boot Manager (P1: TOSHIBA DT...)'

---

### Post by oldfred on 2016-02-08
Toshiba now are like HP & Sony.
They violate UEFI spec that says not to use description as part of UEFI boot. And of course only valid description is "Windows".
There are several work arounds, most use the fallback or hard drive boot entry which uses the /EFI/Boot/bootx64.efi file. When make that file be really shimx64.efi and when you boot hard drive entry you really boot grub's shim file.

Detail command line entries in link in my signature and here (do not use rename of Windows efi file unless you delete Windows and only use Ubuntu):
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
 Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
      
 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)

---

### Post by Chris_Jakins on 2016-02-08
Would all of that be the same for my ASUS PC?

---

### Post by Chris_Jakins on 2016-02-08
So in fear of damaging anything, I may just backup all my files on Windows, erase everything and just install Ubuntu, as that seemed to work well for me before. Later, I can decide to add Windows for dual-boot.

---

### Post by oldfred on 2016-02-08
If you have an UEFI that only boots Windows you still have to do one of the work arounds.
The description check is in UEFI.
You can install in BIOS mode, but UEFI generally better.
If only Ubuntu you can leave Windows folder in ESP - efi system partition and make Windows efi boot really be shimx64.efi. Then system boots system with "Windows" description but really boots shim.

The work arounds work on all UEFI systems as the /EFI/Boot/bootx64.efi is a default way for UEFI to boot. All external devices like flash drives or hard drives use that entry. 
Early versions of UEFI did not include that for internal devices, but all newer UEFI include it as a fallback or default entry as even internal drives may need a second way to boot.

---

### Post by Chris_Jakins on 2016-02-09
I actually have finally got my dual-boot machine working! 

Apparently, GRUB was not installed properly. I ended up having to install grub, then run boot-repair, then update grub which, ultimately, solved my issue. Thanks for your help!

---

