---
title: "ubuntu on pre-installed windows 8"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by windows8wtf on 2013-05-23
I just wanted to install Ubuntu as I did one year ago, could not imagine what mess people have accumulated since then...
Anyway, I think I did what's explained in the first paragraph here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

my log is at paste.ubuntu.com/5692798/

When I boot I only get options "Try Ubuntu without installing", "Install Ubuntu" and something else. The Windows 8 is not visible, the Ubuntu is not visible. Could you help me please?

---

### Post by darkod on 2013-05-23
You can't get a Try Ubuntu option when booting without the ubuntu cd/usb. Where would it offer Try Ubuntu from?

Make sure you are booting from the hdd and see what it says. It looks installed correctly.

Did you disable secure boot and fast boot in bios? Usually people need to do that with win8.

You also might need to create an ubuntu entry yourself in the uefi boot manager. I see some crypt fils on the EFI partition, are you using encryption too? The more complicated the setup, more complicated the uefi dual boot will be. It's problematic by itelf, without encryption into play.

---

### Post by windows8wtf on 2013-05-23
When I try to boot from hdd I get "Selected boot image did not Authenticate" and the laptop shuts down :/ So it is dead without the usb stick.

---

### Post by fantab on 2013-05-24
Disable 'Secure Boot' in the UEFI/BIOS setup. Also disable from Win8 "Fastboot/speedboost". Also if your machine has Intel SRT (smart response technology), you have to disable that too. 

After that, [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") might be able to help you.

---

### Post by ubfan1 on 2013-05-24
Looks like the grub-install was not done with secure boot enabled, so the shimx64.efi (signed by Microsoft) was not put into the /EFI/ubuntu directory (and your efi boot from hard disk does not offer a choice to boot it).  Instead, the efi boot is probably trying to boot a copy of grubx64.efi, and that fails, because it is not signed by Microsoft.  Additionally, the copy of grubx64.efi may not be the one signed by Canonical, which is the one shim needs to continue the boot process.  Try to fix things with a sudo grub-install --uefi-secure-boot  /dev/sda to try to get the right versions installed.  Not sure what boot-repair would do, but I understand multiple runs of boot-repair may be needed to fix things.  Your grub.cfg looks like it got the windows menu items repaired, so hopefully they will allow you to boot windows when you get grub running.

---

