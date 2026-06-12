---
title: "Ubuntu and kubuntu, need to get rid of Kubuntu and keep bootloader"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by rg5million on 2010-11-29
I have Ubuntu installed via wubi

I installed Kubuntu on an actual partition on my harddrive.

I want to get rid of Kubuntu, but when I delete that partition, the bootloader locks up the machine, cause it is missing.

Restore Kubuntu and it works.  On that Kubuntu bootloader, I have the windows option, if I click the windows, then the wubi bootloader kicks in and I can go into ubuntu.

Question:  How can I get rid of Kubuntu and keep the bootloader that allows me to go into Ubuntu.

---

### Post by drs305 on 2010-11-29
You can use the Windows repair disk to reinstall the Windows bootloader (probably fixboot/fixmbr but I'm not Windows savvy). Since Ubuntu is a wubi install, it is controlled by Windows.

If you don't have the Windows repair disk, you should be able to regain the Windows boot with this. Disregard the lilo messages about not being fully installed. The commands assume Windows is on your first drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

When you reboot, it should take you to Windows, where you will have the option of booting Windows or Ubuntu (wubi).

---

