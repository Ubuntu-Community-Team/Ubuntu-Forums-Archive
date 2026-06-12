---
title: "Having Troubling Dual-Booting Asus G75"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by Jason_Reay on 2014-05-11
Installed Ubuntu 14.04 last night, PC loads straight to windows. No Grub, No Boot Menu.     Tried using boot repair, and I get this:

An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/7445405/](http://paste.ubuntu.com/7445405/)

anyone able to help?

---

### Post by oldfred on 2014-05-11
Can you in UEFI menu choose the Ubuntu entry? With secure boot on or with it off?

```
 BootOrder: 0001,0000,0002,0004
Boot0000* grub
Boot0002* Windows Boot Manager
Boot0004* UEFI: Zipp 4GB 1.00
Boot0001* [COLOR=#ff0000]ubuntu[/COLOR],BootCurrent: 0004


```

It looks like you originally installed in BIOS boot mode. And then Boot-Repair converted to UEFI boot.

I see boot repair reporting some grub error. But this says no error with exit code 0
 grub-install /dev/sda: exit code of grub-install /dev/sda:[COLOR=#ff0000]0[/COLOR]

And many then work ok?

---

