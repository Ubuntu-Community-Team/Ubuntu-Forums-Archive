---
title: "Windows 7 fails to (dual) boot from GRUB with &quot;Windows Failed to Start&quot; error screen"
date: 2016-05-08
forum: Installation &amp; Upgrades
---

### Post by TheShreester on 2016-05-08
My PC has Win 7 installed on a  120GB SSD (logical C drive). 
The single "D" drive is a 500GB HDD.

I just installed Ubuntu 14.04 LTS via USB drive 
I used the disk partitioner provided as part of the install process to allocate 200GB of the HDD to Ubuntu leaving 300GB for Windows.
I didn't modify the SSD at all.

Ubuntu installed ok and I can login fine.
However, when I try to boot Windows from GRUB it switches to the white on black 
"WINDOWS ERROR RECOVERY - Windows Failed to Start" error screen 
and neither of the available options (to repair or start normally) works.

Here is my boot repair info: [http://paste.ubuntu.com/16311874/](http://paste.ubuntu.com/16311874/)

Please advise as to what you think the problem might be and how I can fix it.
Thanks a lot!

---

### Post by ubfan1 on 2016-05-08
Were you really booting Win7 in UEFI mode?  Could you have been booting off diskb in legacy mode, (now missing the boot flag on the sdb1 partition)?  Can you change to legacy mode and see what happend when you select sdb for the boot device (maybe you'd have to add the boot flag (back) to sdb1 and maybe sda3).  Looks like a mix-up between legacy and UEFI.  Ubuntu is certainly installed in UEFI mode, and there are certainly Windows UEFI bootloaders present, but looks like a legacy windows boot is on sdb.

---

### Post by oldfred on 2016-05-08
If anything I see it the other way around. But something strange about configuration either way.
Windows 7 is in UEFI boot mode on sda which is gpt partitioned. The sda2 reserved partition is unique to Windows UEFI installs.
But not sure why Windows BIOS boot loader in sdb's MBR. Perhaps old install?
And there is no Windows entry in UEFI for direct boot from UEFI or one time boot key.

And Ubuntu is on sdb in UEFI boot mode, but drive is MBR which is not UEFI standard, but does work. Grub installs to sda's ESP, so Ubuntu UEFI boot from gpt works, but the rest of Ubuntu is on MBR partitioned drive. Better to have both drives gpt partitioned.

Did you reinstall Windows at some point, or was Windows installed to SSD when HDD was still the default boot drive in BIOS/UEFI?

I might use efibootmgr to add Windows boot entry to UEFI and see if that directly boots. Windows may need repairs and either f8 from direct boot, or use your Windows installer or repair disk's repair console to repair Windows. Boot-Repair cannot fix most Windows issues.

       New Windows entry - assumes default sda1  add -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

---

### Post by TheShreester on 2016-05-10
Thanks for both your replies

**oldfred** 

> 
[COLOR=#000000]Did you reinstall Windows at some point, or was Windows installed to SSD when HDD was still the default boot drive in BIOS/UEFI?[/COLOR]

I believe I did have to install Windows twice when I first got the PC. 
It did not come with an OS pre-installed but my first attempt had problems. 
Unfortunately this was a few years ago now so I don't recall exactly what happened or why.
> 
[COLOR=#000000]But not sure why Windows BIOS boot loader in sdb's MBR. Perhaps old install?[/COLOR][COLOR=#000000]
[/COLOR]

If I understand you correctly....
 both Windows and Ubuntu are installed ok 
BUT for some reason my HDD has a MBR with a Windows boot loader which suggests an older (non UEFI) install

> [COLOR=#000000]And there is no Windows entry in UEFI for direct boot from UEFI or one time boot key.[/COLOR]

However, I appear to be missing an entry on my SSD to direct boot Windows from UEFI.
All this time, my Windows was actually booting from the MBR on my HDD (not UEFI) 
BUT GRUB can't find this MBR for some reason?

> [COLOR=#000000]I might use efibootmgr to add Windows boot entry to UEFI and see if that directly boots. [/COLOR]
Hence your suggestion to manually add the missing entry to UEFI to see if that works?

> [COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"[/COLOR]

Running this command via a terminal produced the output below:

BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0004,0000,0001,0002,0003
Boot0000* ubuntu
Boot0001* ATAPI   iHAS124   E
Boot0002* Samsung SSD 840 EVO 120GB
Boot0003* ST500DM002-1BD142
Boot0004* Windows Boot Manager

I will now test if Windows can boot from GRUB and run repairs if possible and necessary.

---

### Post by oldfred on 2016-05-10
The UEFI entry will not help grub, but should let you see if a direct boot from UEFI using one time boot key like f10 or f12 works. Or from UEFI settings with Windows as first choice.

---

### Post by TheShreester on 2016-10-03
After further investigation and going on the replies in this thread I suspect my Windows install is a particularly "funky" mix of UEFI and MBR so when I also installed Linux it somehow broke...

I was able to use my Windows install disk to repair it, allowing me to boot Windows but I can no longer dual boot from GRUB and must instead choose my OS from my BIOS setup. 

As this is a work around rather than a solution I won't close this thread just yet but thanks to all of you who offered advice.

---

### Post by oldfred on 2016-10-03
If you want further review, post a new Summary Report from Boot-Repair.

---

