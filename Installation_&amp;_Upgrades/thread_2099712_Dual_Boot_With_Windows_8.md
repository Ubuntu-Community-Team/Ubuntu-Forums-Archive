---
title: "Dual Boot With Windows 8"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by nayak94 on 2012-12-30
WEll i Had windows 8 installed on my asus k55vm , so i booted into live usb made a 100 gb partition and installed ubuntu
i rebooted adn it directly booted into windows 8. 
so i booted into live usb , tried boot repair which gave an error
here is the link generated 
[http://paste.ubuntu.com/1478921/](http://paste.ubuntu.com/1478921/)

---

### Post by gnush on 2012-12-30
It seems that grub resides on sdb, rather than sda. Is that intentional? I'm not very good with boot-loaders and stuff like that, but try to choose sdb in BIOS the next time you power up your computer. If that doesn't work, install grub on sda and replace the Windows bootloader.

---

### Post by nayak94 on 2012-12-30
> **gnush said:**
> It seems that grub resides on sdb, rather than sda. Is that intentional? I'm not very good with boot-loaders and stuff like that, but try to choose sdb in BIOS the next time you power up your computer. If that doesn't work, install grub on sda and replace the Windows bootloader.

well thanks for your patience, 
im new to all this , its way above my head.
Any links where i can follow up

---

### Post by grahammechanical on 2012-12-30
I am not much of an expert on this either but I guess the sdb is the Pen drive that is being used to collect the data for the printout.

> /dev/sdb1: LABEL="PENDRIVE" UUID="4867-5071" TYPE="vfat"

The question to ask is, Where is Grub? These I think are the relevant error messages.

> No sda6/etc/default/grub
grub-install (GRUB) 2.00-7ubuntu11,grub-install (GRUB) 2.

Reinstall the GRUB of sda6 into the MBR of sda
/usr/sbin/grub-bios-setup: Not found.
grub-install /dev/sda: exit code of grub-install /dev/sda:1

chroot /mnt/boot-sav/sda6 update-grub
/usr/sbin/grub-mkconfig: 237: /usr/sbin/grub-mkconfig: cannot create /boot/grub/grub.cfg.new: Directory nonexistent
umount: /mnt/boot-sav/sda6/dev/pts: not mounted

You might want to make use of this invitation:

> BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. Please report this message to [email]yannubuntu@gmail.com[/email]

Or wait for someone with more experience to offer advice. There is something I remember from other threads on this kind of problem, is to make sure that Fast boot or something like it is turned off.

Regards.

---

### Post by oldfred on 2012-12-30
Even if system is UEFI capable, Windows is in BIOS/MBR mode, so Ubuntu also has to be. 

It looks like install never completed. One of the last steps is the install of grub and grub2's configuration.  Grub did not install to MBR, there is no core.img nor grub.cfg. There is fstab and kernels.

While you can from Boot-Repair chroot into install and do a full install of grub, not just an install of the boot loader to the MBR, it probably is easier just to reinstall. Not sure how easy Boot-Repair's advanced option of full uninstall (will not actually uninstall anything)  & reinstall of grub2 is.

---

