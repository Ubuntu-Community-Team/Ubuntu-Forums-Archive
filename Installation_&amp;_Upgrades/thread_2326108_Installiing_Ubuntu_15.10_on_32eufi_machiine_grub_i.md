---
title: "Installiing Ubuntu 15.10 on 32eufi machiine grub install fails?"
date: 2016-05-28
forum: Installation &amp; Upgrades
---

### Post by johnmccormack on 2016-05-28
Hi getting to the end of my tether with this, have been trying on and off for a month. :-(
as the title says im trying to install 15.10 on a lenovo 2 in 1 by following various guides but on the install it keeps failing on Grub install. other than that it goes through the install process fine. the unit is a lenovo ideapadmiix 300-10iby
main Question is -
Is it possible to install grub manually after the install process fails on grub install 
or could it be as simple as copying the botai32.efi file into the newinstallations boot folder 

I have managed to get a 64 bit version of Debian to install with no problems and boot into it, but after booting it drops me at a command prompt but would prefer to have ubuntu on it if at all possible 
and i should mention that both live-cd's work as they should i have a functioning desktop and internet via a usb dongle.

Any help or insight would be great :-)

---

### Post by ubfan1 on 2016-05-28
That's one of the selling points of UEFI, the bootloaders are just files to be copied with standard tools.  If your live media can boot in UEFI mode, you can just copy its bootloader, in /boot/efi/EFI/Boot/bootia32.efi  (guessing on the name) to your hard disk's EFI partition (same place).  Of couse, you will still the the file /EFI/ubuntu/grub.cfg  for that to work.  Yes, the grub-install may be run anytime, but from your post, I'm not sure if you are running 32 or 64 bit, so it might be possible to install the wrong one.

---

### Post by johnmccormack on 2016-05-29
> **ubfan1 said:**
> That's one of the selling points of UEFI, the bootloaders are just files to be copied with standard tools.  If your live media can boot in UEFI mode, you can just copy its bootloader, in /boot/efi/EFI/Boot/bootia32.efi  (guessing on the name) to your hard disk's EFI partition (same place).  Of couse, you will still the the file /EFI/ubuntu/grub.cfg  for that to work.  Yes, the grub-install may be run anytime, but from your post, I'm not sure if you are running 32 or 64 bit, so it might be possible to install the wrong one.

Thanks For the reply Ubfan1 
its a intel baytrail chip-set/processor which has a 64bit processor and a 32bit uefi 2GB of ram nice little unit for traveling and hopefully tethering to an iPhone for internet. ill give it a go putting the 32bit uefi file into the boot folder don't suppose you know the cli commands for allowing me to write to that folder if i remember correctly i think i try'd to do it but i couldn't figure out how to change the permissions to allow me to write to it -
drwxr-xr-x boot and grub has the same permissions.
could you recommend and good guides for installing grub2 ?

---

### Post by grahammechanical on 2016-05-29
Are you installing 64 bit Ubuntu (AMD64) or 32 bit Ubuntu (i386)? I do not think that 32 bit Ubuntu (i386) is compatible with UEFI boot systems. It might be just secure boot that i386 is not compatible with. Or both. I do not know. I am fairly certain that 64 bit Ubuntu is now compatible with 32 bit UEFI boot systems. But if I am wrong on that, then this might help you:

[https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md)

But you might hit other problems with Baytrail chip sets.

[http://ubuntuforums.org/showthread.php?t=2314964&page=2](http://ubuntuforums.org/showthread.php?t=2314964&page=2)

Regards.

---

