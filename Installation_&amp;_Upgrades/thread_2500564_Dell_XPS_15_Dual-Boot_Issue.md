---
title: "Dell XPS 15 Dual-Boot Issue"
date: 2024-09-05
forum: Installation &amp; Upgrades
---

### Post by mikec96 on 2024-09-05
I am having an issue with my dual boot configuration on my Dell XPS 15. I am dual-booting Windows 10 and Ubuntu 22.04 LTS. 

For some reason, my GRUB menu is not appearing, and instead, I get the message: “the selected boot device failed”. I tried using boot-repair, however, I get the warning that the NVRAM is locked.

I have tried many methods, including:
- Reverting to default settings in the BIOS
- Resetting the NVRAM
- Writing all 0’s to the NVRAM via terminal, followed by resetting the NVRAM again
- Disabling security features (secure boot was already disabled)
- Enabling/disabling TPM
- Enabling/disabling legacy support

I can see the filesystem just fine in a live environment, so there doesn’t appear to be any kind of hardware failure here.

Here’s a link to the pastebin: [https://paste.ubuntu.com/p/4VkHpC73HX/](https://paste.ubuntu.com/p/4VkHpC73HX/)

Could I please get your opinions? Thank you in advance!

---

### Post by oldfred on 2024-09-05
Some systems have UEFI setting to lock NVRAM.
Dell Locked BIOS
[https://ubuntuforums.org/showthread.php?t=2489447](https://ubuntuforums.org/showthread.php?t=2489447)
Locked NVRAM - turning on Secure boot & reset UEFI Dell XPS 9530
[https://ubuntuforums.org/showthread.php?t=2490359](https://ubuntuforums.org/showthread.php?t=2490359)

Dell typically needs UEFI update, if SSD also SSD firmware update. 
But if running Windows, it typically updates UEFI firmware. Not sure about SSD firmware.

If you have UEFI boot entry, you can add this: You could add "--no-nvram" to the "grub-install" command and the "error" should not appear, as the boot entries in the NVRAM are not touched/updated. But you are not showing an UEFI entry.
[https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0](https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0)
[https://blog.fpmurphy.com/2012/12/efivars-and-efivarfs.html](https://blog.fpmurphy.com/2012/12/efivars-and-efivarfs.html)

Or:
Locked NVram
[https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up](https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up) & 
[https://ubuntuforums.org/showthread.php?t=2491460](https://ubuntuforums.org/showthread.php?t=2491460)  &
UEFI settings or include in chroot mount -t efivarfs none /sys/firmware/efi/efivars
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)
[https://ubuntuforums.org/showthread.php?t=2490084](https://ubuntuforums.org/showthread.php?t=2490084)
Locked NVRAM - turning on Secure boot & reset UEFI Dell XPS 9530
[https://ubuntuforums.org/showthread.php?t=2490359](https://ubuntuforums.org/showthread.php?t=2490359)

---

### Post by mikec96 on 2024-09-05
Thank you very much for your help!! Turns out, for whatever reason (probably when I was messing with BIOS settings), the Dell BIOS/system firmware was not pointed to grubx64.efi. Adding that to my boot options solved the problem!

Hopefully someone will read this thread and it will be helpful to them as well. Cheers :D

---

