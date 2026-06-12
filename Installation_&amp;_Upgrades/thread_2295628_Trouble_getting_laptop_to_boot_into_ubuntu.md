---
title: "Trouble getting laptop to boot into ubuntu"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by koekjestrommel1 on 2015-09-20
Hey,

I've got a Toshiba L50-A-1EH laptop, it's about 1.5 years old and has windows 8.1 installed on it. I am trying to install ubuntu 14.03 on it, but it's not booting successfully.

What I did
-burn iso onto DVD
-fast boot off and secure boot disabled in bios/UEFI
-put in DVD and get it to boot to CD
-install ubuntu on new partition, set UEFI partition as device for boot loader installation
-ubuntu installs and when done asks for a reboot
-take DVD out and reboot
-laptop starts into windows 8, no possibilities to start into ubuntu whatsover.

What am I doing wrong?

Cheers,

koekjes

---

### Post by ubfan1 on 2015-09-20
If you use the EFI menu (probably F12? at power-on), select hard disk, select ubuntu, does it boot?
I have an older Toshiba, which worked fine, even with secure boot, but I think the new ones may require a special name like "Windows Boot Loader" on the actual ubuntu boot entry (change it in efibootmgr).  Boot-repair goes one step further, and names the ubuntu bootloader bootmgfw.efi and puts it where the Microsoft bootloader is located.  The other option is to copy grubx64.efi into the default device bootloader location, /EFI/Boot/bootx64.efi.  I found that after a boot failure the bootx64.efi will attempt to boot even before the next entry in the bootorder.  Search this forum for info on the L50, there should be something.

---

### Post by koekjestrommel1 on 2015-09-21
SOLVED BY:
-boot into windows (not like I had another choice anyways)
-run command prompt as admin
type  
> bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
-reboot

And from then on I booted into grub. Both windows and ubuntu seem to be working fine now, so thanks for the reply.

---

### Post by Bucky Ball on 2015-09-21
Excellent. Thanks for sharing and please see the first link in my signature. Enjoy the forums and the OS. :)

---

