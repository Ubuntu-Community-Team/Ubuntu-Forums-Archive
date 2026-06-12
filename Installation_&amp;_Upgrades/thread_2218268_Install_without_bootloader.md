---
title: "Install without bootloader?"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by Melnik_Hoogland on 2014-04-20
Hi,

I have three OS's currently installed on my system and my bootloader is set up the way I like it. I would like to install Lubuntu as well, but I would like to manually run update-grub myself rather than have the Lubuntu installer overwrite the current bootloader. Is there a way to do this? (Note, the computer in question uses UEFI.)

Thanks in advance.

---

### Post by oldfred on 2014-04-20
If it is UEFI, it should just add another folder in the efi partition  and another entry in UEFI menu. But that would not change how you boot with current system. Only if your other install is also Lubuntu should it be an issue.

I would backup efi partition just to be safe, before install.

---

### Post by Luke M on 2014-04-21
I'm assuming you're using BIOS rather than EFI. If you select "something else" and then select a partition instead of a drive (e.g. /dev/sda3) for boot loader installation, then the installer should leave the current grub, or whatever is there, alone (but safest to backup the first 63 sectors).

Regarding EFI install, I think all flavors of ubuntu put their stuff in the EFI/ubuntu directory (not "lubuntu"/"xubuntu"/etc)...so there would be a conflict if you installed multiple ubuntu flavors. Otherwise not a problem.

---

### Post by Melnik_Hoogland on 2014-04-21
> **Luke M said:**
> I'm assuming you're using BIOS rather than EFI. If you select "something else" and then select a partition instead of a drive (e.g. /dev/sda3) for boot loader installation, then the installer should leave the current grub, or whatever is there, alone (but safest to backup the first 63 sectors).

Regarding EFI install, I think all flavors of ubuntu put their stuff in the EFI/ubuntu directory (not "lubuntu"/"xubuntu"/etc)...so there would be a conflict if you installed multiple ubuntu flavors. Otherwise not a problem.

I'm using UEFI. Ubuntu is one of the other installs, so yes I am looking to have multiple ubuntu flavors installed alongside each other.

I've made a backup of the EFI partition. If there does end up being a conflict as you suggest, do you think restoring the EFI partition would likely restore the bootloader setup and still let Lubuntu boot after I run update-grub?

---

### Post by oldfred on 2014-04-21
Restoring entire backup would probably delete the Lubuntu entry UEFI. 
But if installed in UEFI mode any other grub2 for a UEFI install should find it and offer to boot it..

---

### Post by Luke M on 2014-04-21
> **Melnik_Hoogland said:**
> I'm using UEFI. Ubuntu is one of the other installs, so yes I am looking to have multiple ubuntu flavors installed alongside each other.

I've made a backup of the EFI partition. If there does end up being a conflict as you suggest, do you think restoring the EFI partition would likely restore the bootloader setup and still let Lubuntu boot after I run update-grub?

Yes. I would suggest renaming the ubuntu directory to lubuntu and then copy the ubuntu directory from the backup.

If they are the same version of ubuntu, the only difference will be the small grub.cfg file (the real grub.cfg is located in /boot/grub, it's just a pointer).

If you wanted, you could then add a "lubuntu" EFI boot option using efibootmgr (unfortunately not the easiest tool to use...)

---

### Post by Melnik_Hoogland on 2014-04-22
I did the install today and it looks like the Lubuntu installer did overwrite the Ubuntu bootloader, but the result looks okay, everything boots and no need for any repairs or restores. Thanks for all the help.

---

