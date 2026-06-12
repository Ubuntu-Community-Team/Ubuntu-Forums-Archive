---
title: "Windows 8 Disappeard after upgrade to 14.04"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by yehia2 on 2014-04-30
I have an HP laptop that came with Windows 8 installed. I installed  Ubuntu 12.04.1 LTS along with Windows without any problems. Was always  prompted to choose between Win or Ubuntu in the GRUB boot menu. Decided  to upgrade from 12.04.1 LTS to 14.04 LTS. This is what happened:    

----1. Downloaded and started installing 14.04. When it rebooted to  finalize the installtion, it showed a black screen with the words error  and "grub recover>". Nothing else. I was unable to do anything.      

-----2. Used a different computer to create a USB bootable 14.04 LTS  version. Changed BIOS settings to boot from USB. Used the USB drive to  boot and install 14.04 LTS. Installation was completed successfully.       

----3. Changed Boot order back to boot from computer. When I restarted,  there was no GRUB menu, just goes straight to Ubuntu.      

----4. Created a Boot-Repair USB using UnetBootin and ran recommended  repair. After repair, it said "Please do not forget to make your  EFI-BIOS boot on sda 1/EFI/ubuntu/grubx64.efi file!"  I checked the boot  menu, that is not a listed option.   This is the log for the boot  repair :  [http://paste.ubuntu.com/7367458/](http://paste.ubuntu.com/7367458/)      

My question is: 

a. How can I add Windows 8 back to the boot menu                               ?

b. When I click on files, I can no longer mount my hard drives the same  way I could when I was running 12.04.1 LTS?  

Any advice would really  help, as I really need to access the rest of my files. Thanks!

---

### Post by oldfred on 2014-04-30
closed duplicate thread.
Please do not create duplicate threads. We all are volunteers and need to know what others have already told you.

[http://ubuntuforums.org/showthread.php?t=2221080](http://ubuntuforums.org/showthread.php?t=2221080)

---

