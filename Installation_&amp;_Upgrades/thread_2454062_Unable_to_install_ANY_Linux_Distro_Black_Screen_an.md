---
title: "Unable to install ANY Linux Distro: Black Screen and intermitting cursor stuck!"
date: 2020-11-22
forum: Installation &amp; Upgrades
---

### Post by webwiller on 2020-11-22
Hi!
I have a Laptop, an Asus with Intel i4770K 8GB RAM Nvidia 2GB GPU. Not too new but not old at all.
I used to have Win10 from retail (mom's bought it). Then she passed it to me and I started playing around.
I wanted to Dual Boot so I repartitioned the disk with GParted.

Dunno what I done wrong but Gparted closed fine, everything successful and proper shutdown. I started to install Ubuntu 20.10 but after few seconds I get a Asus+Ubuntu screen (which looke dpromising) followed by a lamping cursor in the fist line on the corner up -left.
Stuck.

I thought the USB with Ubuntu was corrupted. Tries again. Same. Tied Mint. Same.
Now even Gparted gives me the same issue. Practically I can't access the PC in any way shape or form to me known (not that there are many...that's why I'm here, lol).

What can I do now?
I think I believed to have somehow meesed up between MBR & GPT & once a flash message about some EFI partition missing appeared as well.

What can I try to log into some OS somehow ?

Thanks in advance for your help, kind regards!
WW.

---

### Post by CelticWarrior on 2020-11-22
Do you want to keep Windows or have only Ubuntu?
If you want Windows you'll have to reinstall it anyway because you already deleted the required EFI partition...

---

### Post by ajgreeny on 2020-11-22
One possible problem you may now see could stem from the fact that you shrunk the Windows 10 partition using gparted; that could cause Windows to be unbootable in future.
It is much safer and strongly recommended to shrink Windows 10 using its own disk management system.  Can you still boot into Windows?

Regarding your installation of various Linux distros I note you have nvidia graphics, so to get a display when installing you will probably need to use nomodeset boot option.
See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for info on various boot options available and how to enable them.

---

