---
title: "Ubuntu 15.10 not booting after installation"
date: 2016-03-07
forum: Installation &amp; Upgrades
---

### Post by Curtis_Johnson on 2016-03-07
Hi guys

After deciding to run Ubuntu 15.10 as my sole OS on my Toshiba Portege R930, I'm now having problems during boot up. 

There seems to be a problem around my UEFI partition from when the laptop was running on Windows 8 and I'm now at a loss on how to fix my problem. 

Are you able to help me solve my boot problem from my paste link? 

[http://paste.ubuntu.com/15322793/](http://paste.ubuntu.com/15322793/)

Any help will be appreciated.

Thanks

---

### Post by grahammechanical on 2016-03-07
What is the problem or problems. You do not say. Please describe the problem.

Boot Repair says that it has successfully re-install Grub. You have a efi boot partition with ubuntu efi boot files. That is as things should be. The efi boot partition also has Windows efi boot files but you do not have Windows on the disk.

Is that causing a problem? What is the problem? Can you load Ubuntu 15.10? As part of the repair Boot Repair set the boot menu to be revealed and wait for 10 seconds before loading Ubuntu. And the boot menus configuration file does not have any option to load Windows. That is as it should be.

Regards.

---

### Post by Curtis_Johnson on 2016-03-07
Thanks for replying. 

After installing Ubuntu 15.10, I took out my liveboot cd as instructed and pressed Enter which then rebooted my laptop. After this it tells me to "Please Insert System Disk" which suggests to me it is still searching for Windows although it is no longer on my laptop? Is there any way i can delete the Windows boot files?

I can load Ubuntu using "try ubuntu before installation" but that it about all i can do currently.

---

### Post by yancek on 2016-03-07
I would change the boot priority in the BIOS back to the internal hard drive where your systems are installed to see if that works.

---

### Post by oldfred on 2016-03-08
Some Toshiba's now are like HP & Sony and have modified UEFI to use description as part of boot. And only valid description is "Windows Boot Manager".

If only booting Ubuntu you can change descption so it thinks it is booting Windows, but use shimx64.efi to boot grub/Ubuntu.
And/or add the fallback or hard drive boot entry /EFI/Boot/bootx64.efi as a copy of shimx64.efi and boot hard drive entry.

 Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair
[/URL]
 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408) 

More details in link in my signature:
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1. 
     sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

