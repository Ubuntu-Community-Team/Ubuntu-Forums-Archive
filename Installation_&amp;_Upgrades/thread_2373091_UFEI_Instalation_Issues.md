---
title: "UFEI Instalation Issues"
date: 2017-10-02
forum: Installation &amp; Upgrades
---

### Post by modar on 2017-10-02
Hey all. I've attempted to install Ubuntu (which I've done successfully many times on other computers) on a HP Pavillon X360 with no luck. Here are the details:

I am installing using usb media using the ubuntu-mate-16.04.3-desktop-amd64. iso

Installation type options:
Erase disk and install
Encrypt installation
Use LVM

The installation goes well until it gets to the installation of Grub 2. It will sit here indefinitely and never complete installation. 

I think that this issue has to due with the damn UEFI because if I manually create an EFI partition and do not use encryption the OS installs perfectly.

Any ideas?

---

### Post by QIII on 2017-10-02
Hello!

Forgive the obvious question, but what happens if you create /boot/efi and use LVM?

---

### Post by ubfan1 on 2017-10-03
I don't use LVM or encryption, but I'd guess you need both an unencrypted /boot (partition) and an unencrypted /boot/efi (the EFI partition) to boot your encrypted LVM.

---

