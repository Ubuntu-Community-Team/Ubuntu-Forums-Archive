---
title: "Stuck trying to install Ubuntu on Samsung 400b Notebook"
date: 2017-08-15
forum: Installation &amp; Upgrades
---

### Post by stewhamilton on 2017-08-15
Has anyone been able to install Ubuntu on a Samsung 400b notebook/laptop? or know for sure that it cant be done so that I can lay this one to rest.

Full model is "NP400B2B-A05UK"

So far I have tried installing from a bootable USB stick, however this appears to be something that is disabled on the motherboard, a security feature possibly? 
I know the USB stick is good as I removed the HDD from the 400B notebook, connected it to another laptop and installed Ubuntu onto the HDD as a bootable drive.
This drive seems to have a fully functioning version of Ubuntu LTS installed as I am able to boot into it when it is connected to the second laptop via a SATA to USB connection by choosing is from the BIOS menu, the Ubuntu bootloader then comes up and I can choose to start Ubuntu. 

My hope was that on returning the HDD to the internal compartment of the 400b and connecting it back in the original internal SATA port it would be recognised on the BIOS as a bootable drive. I tried this and it is, however after this all I get is a blinking underscore "_" on the top left of the screen.

Any help would be appreciated. Thanks. 

I should also mention that when I first recieved the laptop it was running windows 10 and seemed to be working fine. I have since formatted the entire HDD in my efforts to install Ubuntu.

---

### Post by Autodave on 2017-08-15
With Win 10 on there, it should have secure boot and UEFI enabled in the BIOS. Try turning both of those off and see if it will boot then.

---

### Post by stewhamilton on 2017-08-15
Thanks for the reply.
So I tried a number of different options in the BIOS as I initially thought this might be the issue. No luck. 
No reference to a secure boot option in the BIOS anywhere, one of the options was for legacy boot which I have tried both on and off to no avail.

---

### Post by stewhamilton on 2017-08-24
Bump

---

### Post by oldfred on 2017-08-24
Many systems call UEFI Secure boot as Windows or Other. Check your settings.
Did you install in UEFI boot mode?

Some other Samsung and the issues they had.
Boot-Repair in advanced mode with the "use the standard efi file" will do the manual copy of shimx64.efi to bootx64.efi. Then you may be able to boot a hard drive UEFI entry.

 Phoenix SecureCore Tiano bios setup and secure boot is greyed out. You need to set a Supervisor Password in the Security tab
Samsung w/ Phoenix Tiano SecureCore
[http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267](http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267)
Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
 [http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

---

