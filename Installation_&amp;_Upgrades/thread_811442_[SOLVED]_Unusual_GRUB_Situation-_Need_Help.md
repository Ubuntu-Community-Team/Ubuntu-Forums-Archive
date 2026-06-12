---
title: "[SOLVED] Unusual GRUB Situation- Need Help"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by FrostDust on 2008-05-29
Before attempting to install WinXP for dual booting, I had /boot, / and swap on their own seperate partition on the first hard disk of my system. Long story short, I deleted /boot in the process (/ and swap are still there), and I can no longer boot into Ubuntu. The solutions I've read so far seem to involve installing GRUB by copying from a preexisting instance of it into the MBR, or into /boot. Since I deleted /boot, I have no GRUB files to copy from. I seem to be out of ideas at the moment on how to fix this, short of totally reinstalling Ubuntu. Any help on fixing this would be very appreciated.

---

### Post by ssican on 2008-05-29
Maybe, this information will help:

Recovering Ubuntu after installing Windows:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

EDIT
Repairing and Reinstalling Grub:
[https://help.ubuntu.com/community/GrubHowto#head-f60bd54bfea5b5afbbb8eab20586240d973cdde3](https://help.ubuntu.com/community/GrubHowto#head-f60bd54bfea5b5afbbb8eab20586240d973cdde3)

---

### Post by FrostDust on 2008-05-29
Thanks for your help, I managed to get it all sorted out.

I first followed the instructions in [section 5]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-4e903f414fbe7a46a48c7b1ff7ee29c069841a5b") of the first link you provided. While that did provided me with a working GRUB that was able to boot Windows, I was provided with "Error 15: Unable to find files" when I selected an Ubuntu partition. 

Messing around with it a bit, I managed to get it to boot by changing the root device for the boot option to the partition /boot is on, instead of my normal root partition. While it did boot, it then dumped me to a command line, with errors about not recognizing a UUID. When I ran gdm, it had problems finding my home folder, and went back to the login screen. After selecting one of the non-default session options, it booted, but gave me errors about HAL not being initialized, and no internet connectivity was available.

I somehow resolved this by changing my fstab to find the /boot partition by /dev/sda4 instead of its UUID, and copying all the contents of /dev/sda4/boot to my root's /boot.

So, finally, I've got everything up and running happily.

---

