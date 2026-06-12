---
title: "No bootable device error (want to avoid mistakes)"
date: 2019-01-16
forum: Installation &amp; Upgrades
---

### Post by subject031 on 2019-01-16
i got a old acer laptop (a travelmate) and it had no OS on it, so i installed ubuntu and it ran fine, then i installed lubuntu and now i get the no bootable device pop up, im new to ubuntu and i just uninstalled ubuntu/lubuntu and now have the live version on usb for reinstallation, is there a way for me to avoid the mistake i made that made this massive problem in the first place?

---

### Post by yancek on 2019-01-16
Did you install Lubuntu over the previous install of Ubuntu?  Did you install Lubuntu alongside the previous install of Ubuntu on a different partition?  Did you accept the defaults for bootloader installation?  Did you use a usb to install Lubuntu?  If so, after installing did you change the BIOS boot priority back to the hard drive?  What exactly is your end goal?  Do you want to re-install both again?  Is this an older Legacy machine using MBR?


If this is a Legacy machine and you want both Ubuntu and Lubuntu, decide on one to install and when that finishes boot the second OS from the install USB.  You should have GParted on the Live USB which you can use to shrink the partition on which the first OS is insgtalled.  THis will leave unallocated space on which your second OS can be installed.  If this is a Legacy/MBR install, the second install, if left at defaults, will install its bootloader to the MBR and should detect the first system.  If this isn't the scenario you want you will need to post more information.

---

### Post by subject031 on 2019-01-16
i installed lubuntu over ubuntu, i dont remember bootloader default options, i used a usb to install ubuntu but not lubuntu, im not sure about the boot priority but i think it was the hard drive the whole time, my end goal is to just have a working machine with lubuntu and im using a Acer Travelmate well it says its a travelmate but it looks like an aspire, it has both uefi and legacy bios, im not the best in doing this sort of thing, originally it was  a laptop with windows 7 home premium and i got BSODed so i decided to wipe all operating systems on it and start over, i've read that acer laptops have some difficulty installing ubuntu when i've been looking for scenarios similar to mine and after i cleaned all OS's from it again now its being finicky over letting me into the bios menu.

---

### Post by oldfred on 2019-01-16
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If it has UEFI, it  is not really that old.
But how you boot install media UEFI or BIOS is then how it installs. And then you have to have system set to boot in that same UEFI or BIOS boot mode.
Acer in UEFI boot mode as an additional step where you have to enable "trust" on the Ubuntu/grub .efi boot file from within UEFI.

Many also need UEFI update from Acer to have trust setting. 
       
 Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141
      [/URL]
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    [URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]
[/URL]

---

