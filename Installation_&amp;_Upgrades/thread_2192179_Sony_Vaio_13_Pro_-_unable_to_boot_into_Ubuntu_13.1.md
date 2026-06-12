---
title: "Sony Vaio 13 Pro - unable to boot into Ubuntu 13.10"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by gphood on 2013-12-06
[FONT=arial]I've just bought a Sony Vaio 13 Pro and tried to run before I could walk by over-writing the pre-installation of Windows 8 with Ubuntu 13.10. I've installed Ubuntu from a USB, but it won't boot into it. It simply returns to the Sony boot error screen saying that "Your VAIO failed to start Windows" and that the operating system was not found. All I can do is boot from the live USB and access system information from there. I've generated boot info which can be seen at [URL="http://paste.ubuntu.com/6530050/"]http://paste.ubuntu.com/6530050/
[/URL]
I inadvertently deleted the EFI partition along the way, which I've replaced, but I don't know if that's something that's screwed me over. With the benefit of hindsight, I shouldn't have installed over Windows 8, so at least I could have had something working on the machine.
I've not previously done an awful lot with regards to setting up new operating systems, but I've muddled through up to now. I'm out of options now though and I don't really understand what the boot information is telling me.

I've followed the information at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and I've installed and run Boot Repair, which is how I got the report generated in the first place. I tried the repair option on that tool, which carried out the following:
[/FONT][FONT=arial][B]This setting would reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s
[/B]
This didn't make any difference and it still returned to the same error screen when I removed the USB and rebooted.

If I change the boot mode from UEFI to Legacy, or turn off Secure Boot, it won't let me boot from the Ubuntu USB - it just returns to the Sony boot error screen again.

I'd really appreciate any assistance anyone can give me, as I'm currently staring at a very expensive non-working piece of kit :(
[/FONT][FONT=arial][/FONT]

---

### Post by ubfan1 on 2013-12-06
Your information looks like a secure boot setup, which should work with secure boot on.  Do you get a grub menu?  Maybe the grub.cfg file is missing from /EFI/ubuntu/grub.cfg?  You can just copy in the one off the hard disk's /boot/grub/grub.cfg, but the one supplied from the 13.10 install will be better because it is just a stub which pulls in the maintained grub.cfg from /boot/grub.  You can fix that later, or just remember to copy in the new grub when the kernel is updated.  The other thing which might be a problem is does the Sony require (improperly) that the bootloader be named bootmgfw.efi?  boot-repair does have an option to rename the bootloaders, try that after fixing the possible grub.cfg problem.

---

### Post by gphood on 2013-12-09
> **ubfan1 said:**
> Your information looks like a secure boot setup, which should work with secure boot on.  Do you get a grub menu?  Maybe the grub.cfg file is missing from /EFI/ubuntu/grub.cfg?  You can just copy in the one off the hard disk's /boot/grub/grub.cfg, but the one supplied from the 13.10 install will be better because it is just a stub which pulls in the maintained grub.cfg from /boot/grub.  You can fix that later, or just remember to copy in the new grub when the kernel is updated.  The other thing which might be a problem is does the Sony require (improperly) that the bootloader be named bootmgfw.efi?  boot-repair does have an option to rename the bootloaders, try that after fixing the possible grub.cfg problem.

Thanks ubfan1

I can only get to a grub menu if I boot from a live Ubuntu USB I've created, but any changes I make from that screen won't persist next time I reboot. Also, I realised that the recommended fix that Boot Repair carried out didn't persist either, so next time I booted from the live USB, it was back to the beginning again.

I may have a try with a Fedora USB as they have had their binaries signed by Microsoft, which should enable their most recent versions to work on a secure EFI setup. I've tried disabling secure boot in the BIOS and changing from UEFI to Legacy, but as soon as I do wither of these, the laptop will no longer boot from the USB and all I get is the Sony boot failure screen that I've grown to know and hate.

If I get anywhere, I'll post back with the details.

---

### Post by gphood on 2013-12-09
I've had success, but not quite in the way I was expecting. I made a Fedora live USB, but wasn't able to install it. The USB generator I used wasn't set up for Secure Boot, so I changed to Legacy mode with Secure Boot turned off, which did'nt work for me when I tried to run Ubuntu. That all worked fine, but when I tried to reboot I kept on getting an "Operating System Not Found" message. I took a look at [http://www.nicksplace.com.au/2013/07/01/sony-vaio-pro-13-vs-fedora-19/](http://www.nicksplace.com.au/2013/07/01/sony-vaio-pro-13-vs-fedora-19/) and followed his instructions with regards to the grub files - i.e. copying the Fedora grub file to /EFI/Boot and renaming from grubx64.efi to bootx64.efi. This didn't make any difference, so I was back to square one.
I then thought I'd try again with Ubuntu and see if it would boot the live USB from Legacy/Secure Boot off. This time it did. Because I was in Legacy, I cleared all the partitions and did a complete re-install. When it got to restart stage, I pulled out the USB stick and it booted into Ubuntu for the very first time. I don't really know what happened to enable it to start working properly, but I am hugely relieved and hope this helps anyone else in a similar situation. Perhaps the attempted install of Fedora cleared the way for my Ubuntu install to start working properly. Who knows...?

---

### Post by gphood on 2013-12-10
Another quick update - I had problems booting up after I'd initially got Ubuntu running, which appear to have been down to instability caused by the speed of the SSD. This was fixed by pressing 'e' on the Grub menu screen to edit the configuration and on the line starting "linux /boot..." adding "libata.force=noncq" between "quiet splash" and "$vt_handoff" before press F10 to continue booting up.

To make this change permanent, once I'd logged into Ubuntu I edited /etc/default/grub and changed the GRUB_CMDLINE_LINUX_DEFAULT value to "quiet splash libata.force=noncq" and al is now working fine again.

---

