---
title: "Windows 8 upgrade and Ubuntu 12.04 Dual boot"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by dckirba on 2013-01-21
Hello everyone,

I use a Dell Studio laptop that came with Windows 7 and I have set it up to dual boot with Ubuntu 12.04. Microsoft is currently offering Windows 8 Pro upgrades for about 40$ and I am considering upgrading my copy of Windows. I also swore to stick to the LTS version of Ubuntu since it serves my needs well and is a stable, reliable system. 

Now for my questions:

1. Since my laptop is old, does UEFI still apply?
2. Should I wait for the 12.04.2 release before attempting to dual boot (Launchpad lists "Backport UEFI Secure Boot support for Ubuntu 12.04.2" as fix committed)
3. If I use 12.04.1 should I use another bootloader, and if yes, which one?

Thanks for your time,

David

---

### Post by presence1960 on 2013-01-21
> **dckirba said:**
> Hello everyone,

I use a Dell Studio laptop that came with Windows 7 and I have set it up to dual boot with Ubuntu 12.04. Microsoft is currently offering Windows 8 Pro upgrades for about 40$ and I am considering upgrading my copy of Windows. I also swore to stick to the LTS version of Ubuntu since it serves my needs well and is a stable, reliable system. 

Now for my questions:

1. Since my laptop is old, does UEFI still apply?
2. Should I wait for the 12.04.2 release before attempting to dual boot (Launchpad lists "Backport UEFI Secure Boot support for Ubuntu 12.04.2" as fix committed)
3. If I use 12.04.1 should I use another bootloader, and if yes, which one?

Thanks for your time,

David

I took advantage of that offer for the same price. UEFI only applies if your lappie is already booting from UEFI. If you are booting from BIOS you are all set. I did a clean install of Windows 8. You will have to reinstall GRUB because Windows 8 installer will write it's bootloader to MBR. I am booting Windows 8, Ubuntu 12.10 and Sabayon X from GRUB 2 with no problems.

---

### Post by dckirba on 2013-01-21
Thank you :) Now to find a nice free afternoon to fiddle around with the laptop.

---

### Post by presence1960 on 2013-01-21
> **dckirba said:**
> Thank you :) Now to find a nice free afternoon to fiddle around with the laptop.

You are welcome!

---

