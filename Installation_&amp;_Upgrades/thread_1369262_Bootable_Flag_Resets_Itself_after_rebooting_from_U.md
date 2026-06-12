---
title: "Bootable Flag Resets Itself after rebooting from Ubuntu into Windows 7"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by drastrogeek on 2009-12-31
I have a multi-boot system that runs Ubuntu, Windows 7, or Windows Vista. The newer disk, /dev/sda, has both Ubuntu and Windows 7 spread over various partitions. Specifically, Windows 7 takes over /dev/sda1 and the MBR. Then, /dev/sda2 corresponds to the /boot folder in Ubuntu which contains the boot images. Windows Vista is installed on the second disk, /dev/sdb.
 
Now, the Windows 7 installation is only a few days old. The installation set the /dev/sda1 partition to be bootable. After I finished setting it all up, I popped in the original Ubuntu install disk and used the fdisk command to toggle the bootable flag from /dev/sda1 to /dev/sda2 and write the new partition table to disk. When I reboot, I once again see the usual grub menu from where I can either boot into Ubuntu, Windows 7, or Windows Vista. I can successfully boot into any of those three THE FIRST TIME I try it. However, for some reason, after I have booted into Windows 7 ONCE, the bootable flag resets itself back to /dev/sda1. So, the next time I reboot the computer, the grub menu is once again gone and it goes straight to windows 7. 
 
Does anyone have any idea how to stop it from doing this? I have reset the bootable flag from ubuntu several times now and every single time I reboot from windows after that, the problem persists. I have never had this problem before with any other version of windows in a multi-boot system. 
 
Is there something in Windows 7 that REQUIRES that the windows 7 partition be bootable? Is there a way to change this from within windows, since the fdisk approach is clearly not working?
 
Any assistance you can provide would be most greatly appreciated.

---

