---
title: "Install Ubuntu on Beeling Z83"
date: 2016-06-10
forum: Installation &amp; Upgrades
---

### Post by mail-hi on 2016-06-10
Hello to all,


i tried to install Ubuntu 16.04 on a Beelink Z83 Mini PC (Cherry Trail, Windows 10 preinstalled) according to this blog post ([http://www.cnx-software.com/2015/02/13/how-to-install-ubuntu-15-04-on-mele-pcg03-intel-mini-pc/](http://www.cnx-software.com/2015/02/13/how-to-install-ubuntu-15-04-on-mele-pcg03-intel-mini-pc/)). After having copied the "bootia32.efi" to my usb stick, the box booted to a menu where I could select "Install Ubuntu". But after that, the sceen got black and remained black. 

I suppose, this is due to the fact, that the Z83 BIOS does not offer an option for disabling the "SAFE_MODE".

Does this mean, that the Z83 is more or less stuck on Windows or is there a chance to get Ubuntu on it?

Any help is appreciated! Thank you!


Klaus

---

### Post by X-RED_Tech on 2016-06-10
Ubuntu 16.04 shouldn't need "bootia32.efi" nor disabling secure boot. Ubuntu has been digitally signed since almost the beginning, when it emerged as new requirement for UEFI hardware.
Also as far as I know the 32-bit EFI file was needed in previous releases but only for "Bay Trail" CPUs like the one found in your guide, not for others.

That said, I suggest you use a standard ISO as downloaded from Ubuntu website. Do not add the additional EFI file and just boot it as we always did. You might see better results.

---

### Post by mail-hi on 2016-06-12
[COLOR=#000000]Thank you for your help, but without this "bootia32.efi" file, the Z83 does neither show me the GRUB menu nor boot up. With "bootia32.efi", at least GRUP comes up. 
In the meanwhile I tried the 14.04 LTS distribution from Ian Morrision...without success. As this image already contains "bootia32.efi", GRUP comes up, but after selecting "Install Ubunto" the screen gets black and remains black. 

Maybe there are some boot parameters, that allow Ubuntu to boot on my box?
[/COLOR]

---

### Post by gordintoronto on 2016-06-12
Have you tried nomodeset?

---

