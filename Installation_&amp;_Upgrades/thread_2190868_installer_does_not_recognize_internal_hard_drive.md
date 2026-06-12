---
title: "installer does not recognize internal hard drive"
date: 2013-11-29
forum: Installation &amp; Upgrades
---

### Post by jjjjswait on 2013-11-29
hello,

I've installed various distributions of ubuntu and other debian-based operating systems on multiple computers in the past and have never had any problems with single- or dual-boot installations until today.
I'm trying to make a dual-boot with windows 7 on my parents computer at their request and, though the windows installation went flawlessly, have not been able to install ubuntu to their new HP Pavilion HPE h8-1230 PC tower.
I'm able to boot into live sessions (I've tried ubuntu 12.04 lts, 10.10, 13.04, and xubuntu 12.04) but, when trying to install the OS, on the 'Installation Type' step no hdds are listed for me to install to/partition for dual-boot. However, in the live session I am able to navigate to the internal hdd in File Manager.
I'm not sure if this is in some way related to RAID or UEFI configuration as I've never had to mess around with that in previous installations.  I've tried booting to both the UEFI- and non-UEFI-enabled options for my usb drive in the BIOS boot menu, but no luck.
I can easily reinstall windows with a new hdd configuration is necessary, I just want to figure this out for them before I leave (thanksgiving visit) tomorrow.  Please help me save face and complete what should be a simple install. 
Any help is appreciated, I'm at a loss here.

Thanks in advance.

---

### Post by heir4c on 2013-11-29
have you disabled secure-boot?
And what you see if you use gParted? Can you see the HD and if so, can you make changes to the partitions?

---

### Post by jjjjswait on 2013-11-29
hi, thanks for the response,

secure-boot is disabled.  in gparted i can see the hdd (both primary and 'system reserved' partitions) and seem to be able to make changes to them

---

### Post by heir4c on 2013-11-29
I think you have already 4 partitions, because of the UEFI on your system. 
You must remove 1 of the partitions and make a Extended partition of the deleted partition. 
Backup everything that is on that partition!!! And make a recovery-dvd for Windows, so you can rescue Windows if needed.
Don't delete the first 2 partitions. That is the boot partition and the system partition of Windows. (You can resize the partition with the Windows system on if you want, but NOT the first with the bootloader (or something like that) on.)
I have no experience with UEFI (and I don't use Windows) so if you want more info, look for it on Google or in the Ubuntu-Wiki/Documentation.
Take your time to do every step.

Succes!!!
Greetings
Gerolf

---

### Post by jjjjswait on 2013-11-29
I'm pretty sure that there are only two partitions on the drive; both gparted and windows' disk management tool only show the primary (full size of drive minus 100mb) and system recovery (100mb) partitions.  do you mean that I should resize the primary partition within gparted and then attempt installataion?

thanks

---

### Post by jjjjswait on 2013-11-29
well, I was able to get ubuntu to recognize the hard drive by using, in a live session, the command
sudo dmraid -rE
ubuntu is apparently installed, but there is no grub menu on reboot, just windows boot manager.  I'm trying to figure out how to boot to grub by following the instructions on this page: [http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)
no luck yet.

if anyone has any ideas, please let me know.  it seems that windows has even stolen BIOS from us...

thanks

---

### Post by fantab on 2013-11-30
Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")... 'Recommended settings' should do. Make a note of LINK which Boot-repair creates for 'BootInfo Summary' and post it here, if there are still problems booting Ubuntu.

---

### Post by jjjjswait on 2013-11-30
hi fantab, thanks for the suggestion.  I followed the directions for  boot-repair, and now the machine boots to grub, but windows isn't an  option, only ubuntu and ubuntu recovery mode.
a cursory google search  hasn't led me to anyone with a similar problem, but it seems like i'm  getting closer to making this work.  any ideas?  
the url at the end of the boot-repair process was 
 [http://paste.ubuntu.com/6500448/](http://paste.ubuntu.com/6500448/)
thanks for your help

---

### Post by jjjjswait on 2013-11-30
also, I tried selecting 'windows boot manager' in boot options, but it still goes to the ubuntu-only grub menu

---

### Post by oldfred on 2013-11-30
It seems you have a newer computer that also boots in UEFI mode, but your installs are in BIOS mode with MBR(msdos) partitioning.
Boot-Repair says it booted in UEFI mode. Ubuntu will offer to boot in UEFI or BIOS mode from the UEFI menu. Since all your installs are BIOS you need to always boot in BIOS mode.

Not sure why it did not pick up Windows. Is it hibernated, or did you resize from the installer which turns on chkdsk flag? Those flags prevent Linux NTFS driver from mounting the NTFS partitions, so os-prober may not find the installs. Otherwise Windows looks correct and os-prober should find it. 

If flag(s) are set you may have to directly boot Windows. You would then need to use Boot-Repair, turn off auto update, and in advanced options choose Windows and sda to update boot loader. If Windows then boots and makes its repairs you should be able to again run Boot-Repair and update to install grub into sda's MBR.
Or you can use your Windows repairCD or flash drive to run chkdsk on both sda1 & sda2.

---

### Post by jjjjswait on 2013-11-30
i'm not sure why, but when I re-connected the data drive (i had disconnected it for ease of installation; it had an old installation of windows on it), upon rebooting, grub recognized the new windows installation along with ubuntu.  problem solved!
thanks for your help, guys

---

