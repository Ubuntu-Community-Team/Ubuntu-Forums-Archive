---
title: "installed lubuntu 13.04, boots straight to Windows 7"
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by grey-area on 2013-08-18
tl;dr I thought the Lubuntu 13.04 installation CD that I burned was booting into UEFI mode and performing a UEFI install. Looks like it was booting in a legacy/BIOS mode and not performing a proper UEFI installation. I created a Lubuntu 13.04 installation USB stick, verified that the USB stick was booting in UEFI (by checking for the existence of /sys/firmware/efi) then performed the installation again. Now the ASUS laptop gives me a UEFI boot option for GRUB in the boot menu (accessed by pressing ESC after powering on when the ASUS logo splash graphic is displayed).


Well I thought I had this figured out but it is not working as intended.

I am trying to install Lubuntu 13.04 alongside Windows 7 (which is already installed on my ASUS laptop) on the single internal HDD. I backed up my system, and even ran BootInfo off the latest boot-repair-disk:

[http://paste.ubuntu.com/5997315/](http://paste.ubuntu.com/5997315/)


Notice down at the bottom it says "EFI detected". I had the partition table setup and everything looked okay. I installed Lubuntu 13.04 from CD, installing the boot loader on /dev/sda1, the partition identified as the EFI partition (was that the wrong thing to do)?

Now when I power on the system, it boots straight to Windows 7. Clearly I was expecting a GRUB menu. Here is BootInfo taken after the Lubuntu install:

[http://paste.ubuntu.com/5997315/](http://paste.ubuntu.com/5997315/)


I know my way around SysV Unix, Solaris and Red Hat pretty well. I am still learning Ubuntu/Lubuntu but have been using it for about 3 years.

UEFI is new territory for me, although I have read most of the docs on these forums about UEFI and Ubuntu installs. Any help being able to get the system to dual boot Win7 + Lubuntu would be appreciated.

Thanks.

PS - In case I was not clear, I have not ran "Recommended Repair" from the boot-repair-disc yet, only BootInfo.

---

### Post by steamer360 on 2013-08-18
Have you tried removing the partition and then reinstalling, or is that not an option at the moment? Have your tried a usb stick, it might be a cd issue. I have not come across this issue myself, so that is all the insight I have in the matter.

---

### Post by grey-area on 2013-08-18
Which partition do you mean? The EFI partition? Or the Win 7 partition?
 
No, I have not tried USB stick. I think that is my next step. I just realized that the Lubuntu 13.04 CD is booting in BIOS mode, not UEFI.

---

### Post by grey-area on 2013-08-18
Thanks, your suggestion worked. GRUB now shows up as a UEFI boot option. I thought the Lubuntu 13.04 installation CD disc was booting in UEFI mode but it turns out it was booting in BIOS and was not doing a proper UEFI installation of Lubuntu.

I used Unetbootin to create a installation USB stick and everything worked fine after that.

---

