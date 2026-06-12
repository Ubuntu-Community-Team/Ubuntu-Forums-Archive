---
title: "How to enable OEM install for UEFI Boot"
date: 2020-05-07
forum: Installation &amp; Upgrades
---

### Post by bobsmithlx on 2020-05-07
I've created a USB boot drive and can install in OEM mode fine when using legacy BIOS (Hold F4 at boot prompt),

If I boot a fresh install via UEFI, Ubuntu loads live to the GUI and the only options available are "Try" or "Install"

How can I get the option of an oem-install when booting from UEFi please?

Thanks

---

### Post by CelticWarrior on 2020-05-07
I think you can just install and customize with a temporary user and finally install and run 'oem-config' and shutdown. The next boot should ask for setting up username, password, etc.

---

### Post by C.S.Cameron on 2020-05-07
Can you not just add ```
oem-config/enable=true
``` to the **linux...** line in your grub.cfg file in your EFI boot partition?

---

### Post by bobsmithlx on 2020-05-08
Thanks, I didn't realise that the EFI boot basically auto ran the first option in grub.cfg to launch Ubuntu Live GUI.

I Added oem-config/enable=true to the other menu entries in the grub.cfg and UEFI boot now loads into the GUI with manufacturer mode install enabled.

Thank You.

---

