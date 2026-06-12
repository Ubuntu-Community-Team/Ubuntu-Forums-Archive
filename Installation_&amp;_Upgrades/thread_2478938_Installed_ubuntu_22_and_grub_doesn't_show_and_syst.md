---
title: "Installed ubuntu 22 and grub doesn't show and system beeps like crazy"
date: 2022-09-09
forum: Installation &amp; Upgrades
---

### Post by archimedes1981 on 2022-09-09
I had ubuntu 18 and decided to format / and keep /home partition. I installed ubuntu budgie 22 and Linux mint 20, both are beeping like crazy on boot, but boot fine although very frustrating and humiliating. Don't know if anything else is wrong cos barely logged in. Re installed like 5 times with different options. With efi partition and without, with boot device as sda1 and as "ssd name". Can't find an option to make a bootloader partition but never had one. In mint if I press shift, grub loads and it doesn't beep. In budgie I noticed it saying something like" mtd device must be supplied (device is empty) "

---

### Post by oldfred on 2022-09-09
Most find this error/warning, does not effect boot.
mtd device must be supplied
[https://ubuntuforums.org/showthread.php?t=2476796&page=3](https://ubuntuforums.org/showthread.php?t=2476796&page=3)
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622)

You should not mix UEFI/gpt and BIOS/MBR.
So are both systems UEFI with gpt partitioning?
Do you have latest firmware for UEFI and if SSD latest firmware?
Have you checked UEFI settings? Beep could be that it is not booting in default mode & switching to alternative. 

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by archimedes1981 on 2022-09-09
I think I'm following although I can't see what I could have done wrong except from creating an EFI partition when installer warned me to. I'm using a DE inspiron N5030 which is quite dated and probably desn't support UEFI. previous Ubuntu 18 worked fine.
the bootinfo link is:
[https://paste.ubuntu.com/p/G9TzR9Sn9h/](https://paste.ubuntu.com/p/G9TzR9Sn9h/)
This bootinfo thing is new to me. Who can access this? It seems quite detailed and specific.
I looked it up and did what the website said so I did this when booted from live USB, not when booted regularly.

---

### Post by oldfred on 2022-09-09
Details lets us know how your system is configured to boot.

You show old MBR partitioning. That now is only required if you have to boot Windows in old BIOS mode.
The newer gpt is normally used with UEFI boot, recommended by UEFI & required by Microsoft for UEFI boot of Windows since 2012.
You can use gpt with BIOS, I have since about 2010 on old BIOS only system.

You show two versions of grub, but only one install. One grub is in MBR for BIOS boot and one in ESP for UEFI boot. But typically only one is valid and trying to boot in other mode uses an invalid grub and fails to boot.
It looks like you are currently configured for UEFI boot as fstab has mount of ESP - efi system partition. So you need to have system set to boot in UEFI mode by default, not old CSM/Legacy/BIOS mode.


Google says your model came out in 2010. Microsoft required UEFI/gpt starting in 2012, so bit surprised you have UEFI install.
Early UEFI often had issues. UEFI updates & Linux kernel & driver work arounds got most early UEFI to work. But back then many stayed with BIOS as they were more familiar with it.

You only show Ubuntu 22.04.1 in sda7.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Report showed this:
> BIOS/UEFI firmware: A02(0.2) from Dell Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).

If system if UEFI, it probably needs UEFI update from A02.

To repair system, you have to be booted in the mode you want to repair. 
So for UEFI repairs, boot in UEFI mode or for BIOS repairs boot in BIOS mode.
You may then need to total reinstall of grub using Boot-Repair's advanced mode. And/or UEFI/BIOS settings to match grub's install boot mode.

---

### Post by ne29914 on 2022-09-09
The "mtd device must be..." error on boot is known and at this time has NOT been fixed. It's not catastrophic, but _very_ annoying.

---

### Post by archimedes1981 on 2022-09-10
So what would happen if I just deleted the EFI partition?
I can't change to GPT cos my /home partition is in MBR and I want that, plus I can't change the BIOS to EUFI cos it's too old. I believe my only way is to proceed with MBR. I won't need any of the GPT features anyway.

---

### Post by yancek on 2022-09-10
The boot repair output beginning at line 16 shows the boot files for UEFI and indicate Ubuntu but Mint may also use the name ubuntu in UEFI.  You indicate in your initial post that Mint boots but Ubuntu does not, is that correct?

You have a Legacy install with Linux filesystems on sda6 and sda7,  shows sda7 as the system partition with Ubuntu 22.04.  Is sda6 your /home partition or the Mint partition?  Line 96 shows no OS.  I see now on line 200 that sda6 is your /home partition.

Beginning at line 76, boot repair shows the system is apparently UEFI capable.  Have you checked your BIOS firmware for any reference to UEFI?

>                            So what would happen if I just deleted the EFI partition? 

I'd suggest checking your BIOS for references to UEFI before you do that.  You do have Grub in the MBR pointing to sda7 so if the drive is set to Legacy, it should boot but the information in boot repair would indicate it would boot Ubuntu on sda7.  A safer option would be to comment out the /boot/efi entry in the /etc/fstab file by placing a # at the beginning of that line.

Beginning at line 95, boot repair shows only sda7 with an OS installed.  Looking over your posts again, it isn't clear if you are actually able to boot only that you see the Grub menu.  Are you able to boot Ubuntu or Mint?  It is possible to do an EFI install on an MBR/Legacy drive but is not the standard nor is it recommended.

---

### Post by archimedes1981 on 2022-09-10
I'm not using dual boot. I'm only installing one system but since the ubuntu installed gave me this beeping issue I tried installing mint instead mint responded the exact same way with beeps followed by boot. I switched multiple times and used 3 different OSs but using the same partition sda7 and same /home sda6 although I tried sometimes with an EFI partition sda1 and sometimes without. They all boot but they beep a lot during boot. That issue seems unchanged which makes me think that even if I delete the EFI partition it would still happen. I checked the bios and it doesn't  mention UEFI.

---

### Post by oldfred on 2022-09-10
Most UEFI are still called BIOS by vendors even though it has been UEFI since Microsoft required UEFI/gpt boot starting in 2012.

I think the beeping is related to boot mode.
Or system is tying to boot in UEFI mode (or BIOS), cannot find UEFI boot file for Windows, beeps & goes to next in default boot mode or beeps to switch boot modes.
Some vendors only want to boot Windows, especially with early UEFI.

---

### Post by archimedes1981 on 2022-09-11
OK. So I fixed the beeping by re installing GRUB with the Boot-repair live USB. The only problem now is that it stops on grub and I have to choose Ubuntu to boot. Otherwise it stays in Grub forever. There is no timer. I modified /etc/default/grub with vi and also downloaded GRUB-customizer but even after running update-grub, the changes don't take. I modified the time and background colours but nothing happened. I deleted the sda1 EFI partition now but still nothing. I mean I can work but system won't boot unless I tap space or enter at grub. [https://paste.ubuntu.com/p/Bqf3Xfc42P/](https://paste.ubuntu.com/p/Bqf3Xfc42P/) .

---

### Post by archimedes1981 on 2022-09-11
I'm now starting to think that this is not going to go away. I've changed GRUB_TIMEOUT_STYLE= from menu to countdown and instead of a menu at grub i just get a countdown at the end of which.......drum roll...........no seriously, guess.......................I get the faithful annoying beeps and then boots. I changed it back to menu and we're back to no beeps and menu but no autoboot.

---

### Post by archimedes1981 on 2022-09-18
So I turned it back on again today and the beeps are back along with the grub menu.

---

### Post by archimedes1981 on 2022-09-18
I switched BIS from AHCI to ATA and it seems to have worked.

---

