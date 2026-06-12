---
title: "Windows 10 Didn't Appear After Installing Ubuntu"
date: 2020-05-07
forum: Installation &amp; Upgrades
---

### Post by ichsanm669 on 2020-05-07
Help!!!

I tried to install ubuntu dual boot with windows. Ubuntu has been installed but at boot time, the windows are gone. I tried to press f9 to select boot, but whatever I pressed it ended up with ubuntu. 

It seems I don't know about partition schemes and I immediately made a ubuntu usb bootable from windows. When installing ubuntu dual boot on the partition menu, I have seen in many tutorials that there is a Windows inscription in the tab or column "System", but in me there is nothing written on rows sda 1, sda2, or sda 3 which are all three are windows partitions. I made swap, home and efi partitions, all new logical partitions from free space to install ubuntu.

I have tried deleting all the partitions for Ubuntu, but when I restarted, no boot devices were found. I also tried boot repair but still didn't bring up my windows menu again. What should I do to bring up windows again?



This is the url from boot repair
[https://paste.ubuntu.com/p/6FR58W45f9/](https://paste.ubuntu.com/p/6FR58W45f9/)

---

### Post by yancek on 2020-05-07
Line 7 of boot repair states "The disk contains an unclean file system (0, 0)" which means you have left fastboot and/or hibernation on in windows and no Linux OS will mount a hibernated partition due to the likelihood of data loss.  You will not be able to access a hibernated system and therefore it is impossible to add an entry to grub.cfg for windows with Ubuntu Grub or boot repair.  You can NOT turn off hibernation in windows from any Linux so you will need your windows installation DVD or similar software (Recovery CD) to do that.  Also, run chkdsk.

You have a Legacy install of windows and an EFI install of Ubuntu and that is a bad combination when both systems are on the same drive.  Since windows is a Legacy install, you need Ubuntu as a Legacy install and not UEFI.  Your hardware is UEFI capable but the windows install is NOT UEFI so make sure that Legacy/CSM boot is enabled in the BIOS.  Probably the simplest thing to do is to re-install Ubuntu in Legacy mode after removing the EFI partition (sda7).  The link below to the Ubuntu documentation explains some of the problems you encountered as a result of mixing an EFI install with a Legacy install.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-05-07
When you installed Ubuntu in UEFI boot mode with an ESP, the ESP has the boot flag & esp flag.
But BIOS boot mode Windows boots from MBR to NTFS primary partition with the boot flag that has Windows BIOS boot files. The ESP is not primary, not NTFS nor has BIOS boot files.
So you cannot have UEFI Ubuntu & BIOS Windows on same drive.

Move boot flag back to sda1 and Windows should boot. Otherwise you need further Windows repairs.

Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012. It did allow BIOS/MBR configuration as some large customers wanted that capability.

---

