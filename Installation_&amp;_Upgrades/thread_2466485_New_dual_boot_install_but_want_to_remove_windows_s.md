---
title: "New dual boot install but want to remove windows sd card for simplicity."
date: 2021-08-28
forum: Installation &amp; Upgrades
---

### Post by bulgin on 2021-08-28
Hello.

Wishing the very best to you all and those you love.

I have a laptop with dual boot working fine.  It's Ubuntu 20.04 alongside Windows 10.  Grub boots up and I can choose.  As I now want to LVM encrypt the new ubuntu-20.04.3-desktop-amd64.iso and understand this can be complicated to preserve alongside Windows I'm thinking of doing the following and could use some sage feedback.

The Ubuntu installs are only in the hard drive that came with the laptop and the windows install is only on an sd card installed inside the laptop.

If I remove the windows sd card then do a new LVM encrypted ubuntu-20.04.3-desktop-amd64.iso, and then put the sd card with windows back in place, will this mess up the boot process?  I'm thinking not but I'm not always thinking straight, too.

So some guru advise would be much appreciated.

---

### Post by tea for one on 2021-08-29
Is the SD card soldered to the motherboard?

If the Windows drive is [COLOR="#0000FF"]easily[/COLOR] removable, then you should be able to boot via the UEFI boot menu when it is returned to its original location.

Possibly, you can isolate/de-activate the Windows drive in your UEFI firmware?

When playing around with multiple operating systems and drives, it is essential to have data back-ups and also access to your original installation media.

e.g. Windows 10 ISO and Ubuntu ISO on bootable devices.

---

### Post by grahammechanical on 2021-08-29
There is a small point that I am confused about. Are you intending to do a new install of Ubuntu 20.04.3? It does not matter much if this will be two installs of Ubuntu or a new install over the original Ubuntu installation. The install process will install a new copy of the Grub boot loader which will not have Windows 10 in its menu because the Windows 10 drive is not present.

So, when you re-insert or re-activate the Windows 10 SD card you should boot into Ubuntu and run this command:

```
sudo update-grub
```

The boot loader program will then scan all drives looking for operating systems and you will then get Windows 10 in your Grub boot menu.

Regards

---

### Post by bulgin on 2021-08-29
Thank you Tea For One.
I can easily deactivate that drive in the boot menu and it is not soldered into the motherboard, can easily remove. I have backups and more than one.  Thank you for your advise.

---

### Post by bulgin on 2021-08-29
@grahammechanical thank you for that idea.  
That does seem like the best approach.

---

### Post by oldfred on 2021-08-29
UEFI may forget UEFI boot entry from a drive that is removed.
Most UEFI do find Windows entries automatically, but not Ubuntu entries.
And most now boot from a fallback or drive entry that will just show drive name, but boot from /EFI/Boot/bootx64.efi.
With Windows bootx64.efi is just a copy of Windows UEFI boot file. Grub often overwrites that with a copy of shimx64.efi for UEFI boot with Secure boot on or off. 

Note that Ubuntu's Ubiquity installer only install grub into ESP on first drive. Usually that is the ESP - efi system partition on the Windows drive. If you remove or disable the Windows drive, then you need an ESP or if full drive install, the installer will create an ESP on that drive.You may not now have an ESP on Ubuntu drive.

If you do not disconnect Windows drive, you can totally install to second drive. Very old bug, several work arounds, but never really fixed.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26) Need ESP on second drive.
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

This is also in bug report:
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079)

---

