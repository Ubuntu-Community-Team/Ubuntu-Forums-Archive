---
title: "Unable to Select Partitions during Ubuntu 16.04 Live Boot Installation"
date: 2019-01-12
forum: Installation &amp; Upgrades
---

### Post by nancibles on 2019-01-12
Hey Everyone! 

I'm new to Ubuntu and I'm trying to install Ubuntu 16.04 onto my laptop. I'm using a USB to install it, which worked on an older laptop, but when I'm going through the installation process on my Dell G5 (currently with Windows), it seems the installer doesn't recognize the partitions and I can't select one to install it onto. I've tried doing some things suggested in other forums like turning hibernate off and turning the fast startup off with no success. I'm hoping someone here might know if there's a way to fix this that doesn't involve re-installing Windows? Any help would be greatly appreciated and I've added some pictures that might help to explain my problem better. 

Thanks! 

From the Installer:

[ATTACH=CONFIG]282183[/ATTACH]
[ATTACH=CONFIG]282181[/ATTACH]

from GParted:
[ATTACH=CONFIG]282182[/ATTACH]

---

### Post by TheFu on 2019-01-12
If the partitions are still marked as open by Windows, then Linux won't touch them.  I'd double check that.
Inside Windows, have you shrunk the partitions to make room for 2 needed by Ubuntu?  1 for swap and 1 for / (everything else).  BTW, more partitions are usually a good idea, so you can have /home/ on a partition itself.

What sort of storage does the machine have?  SSD, NVMe, SATA disk or something else?

Also, can you be a little more specific on the exact model of Dell?  I have a Dell 1558, for example.

---

### Post by oldfred on 2019-01-12
Almost all new Dell systems need UEFI update and SSD firmware update.
Dell also has drive set to RAID (even if one drive) or Intel SRT, that need to be AHCI in UEFI. But if using Windows you need to install the AHCI driver first.
If you have nVidia card/chip, you will need nomodeset boot parameter to install & first boot or until you install nVidia driver from Ubuntu repository (not .run from nVidia).
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

In Windows make sure Windows fast start up is off. That sets a hibernation flag that prevents the Linux NTFS driver from seeing NTFS partitions.

Dell issues are pretty common across many models. Bigger differences if AMD or Intel based.

       Dell update UEFI/BIOS from Linux
[URL="https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en"]https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en

[/URL]Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 

See link in my signature below for general UEFI install info.

       Dell XPS 16 9570 Personal experience of installing Ubuntu 18.04 LTS
[https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe](https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe)
[https://ubuntuforums.org/showthread.php?t=2408749](https://ubuntuforums.org/showthread.php?t=2408749)
[https://ubuntuforums.org/showthread.php?t=2408585](https://ubuntuforums.org/showthread.php?t=2408585) 
    
[URL="https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en"]
[/URL]

---

### Post by nancibles on 2019-01-14
I was able to get things working, following oldfred's blog post with changing to AHCI with my Dell G5587 which has SSD storage. Thanks!

---

