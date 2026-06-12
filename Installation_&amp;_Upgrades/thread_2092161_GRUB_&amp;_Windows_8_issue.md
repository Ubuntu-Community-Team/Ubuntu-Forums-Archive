---
title: "GRUB &amp; Windows 8 issue"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by neonfire999 on 2012-12-06
Ok, so I created a 25gb partition on windows 8 and then since windows 8 wouldn't let me boot into the live linux mint 14 cd, I ran the exe on the cd and told it to help me boot into the live cd. When it did, I went ahead to install it and selected to install alongside windows. When it finished installing and everything, I went to boot into windows 8 again through grub and now its giving me an error that says "error: device format 'ldm/XXXXXXXX/Volume 1' invalid: must be (f|h)dN, with 0 <= N < 128" and then says "a disk error occured. press ctrl+alt+del too restart". When I try to boot into the recovery partition it just shows the second screen. I tried to boot into my windows 8 installation disk to try to repair the boot record, but like i said before, it won't let me boot into cds or dvds for some reason even though ive put them at the top of my boot order. Thanks for the help! I have an essay to write that is due tomorrow (friday) and i'd really like to have this fixed quickly so I can get to that..

---

### Post by oldfred on 2012-12-06
Was Windows 8 hibernated?  Oh silly question Windows 8 is always hibernated and hibernation causes boot issues.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

    
What computer? 
You need to check manual on forcing your was back in the the UEFI/BIOS or even restore the UEFI /BIOS. 
Sometimes just a full power down including removing battery. 
Some have had to access motherboard and jumper two pins to totally reset UEFI/BIOS. But again check manual or search for details on your system.

Also some instructions from an older HP UEFI instructions.

> System Diagnostics: Press the Esc key when the “Press Esc for startup menu” message displays when
you boot the computer. Then press F2 to launch System Diagnostics. F2 will not wake the system
from the off state or the Sleep/Hibernation state. F2 can be used only during POST when the BIOS
keys are displayed.
BIOS Recovery: Hold down the four arrow keys, and then press the power button to launch BIOS
Recovery.


---

### Post by Daystar1124 on 2013-06-09
Sorry to resurrect this, seeing as it is a few months old.. but was there a resolution to this problem? 

Originally, I suspected that I had somehow corrupted my windows 8 install.. (error showing this in Ubuntu gparted) but after reinstalling it and still having the same problem I am dumbfounded. I have used grub 2.0 for dual-booting OS on machines before, but this is my first time deciding to boot with ubuntu13 and Win8. I assume this is a problem with grub and not with Win8, but I am really unsure. Did OP have success in any of the mentions for the other guy? I receive the same error message he described.. 

HP Pavilion DV7. Windows 8 on sda1, unbuntu13 on sda3 with swap on sda4. Windows loaded fine prior to installing ubuntu13 and grub. Grub loads everything perfectly, like before, but fails on Win8. I tried two installs:

First: creating the partition myself within windows and selecting that partition during install. 
Second: Merging my partitions and allowing ubuntu installer to auto-partition my drive. 

Both obviously failed. I dont have a UEFI system so im not sure what settings you guys are changing to get these other options cleared. And now, I cannot boot windows 8 to look for a secure boot option?

---

### Post by oldfred on 2013-06-09
@Daystar1124
If you are booting with BIOS not UEFI, you do not have secure boot. Only Windows 8 pre-installed is UEFI with secure boot turned on.
But all Windows 8 systems are always hibernated for fast boot.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)


 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

---

