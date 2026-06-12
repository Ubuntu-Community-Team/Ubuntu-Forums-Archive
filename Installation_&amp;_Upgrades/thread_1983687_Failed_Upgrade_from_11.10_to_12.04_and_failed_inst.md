---
title: "Failed Upgrade from 11.10 to 12.04 and failed install of 12.04"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by abstractAlchemist on 2012-05-20
Just got a new computer, tried to install ubuntu 12.04 ( after installing windows 7 in UEFI mode ), and the installer just freezes  in UEFI mode after selected both the install option or try without installing option.  I also tried installing 11.10 in UEFI mode ( no problem ), then upgrading to ubuntu 12.04, and after what appeared to be a successful install, everything became completely unresponsive, and after the restarting, refused to start up.  

Legacy bios mode seems to work fine, but UEFI just goes down the toilet, which is fine for one out of three computer i'm running.

Hardware Information
Asus Rampage IV Formula Motherboard
Intel i7 3930K 3.8GZ ( I think )
NVidia Geforce 580 GTX 3087MB
Corsair Dominator GT 4GB DDR3 2133 MHZ
2x OCZ Agility 3 128GB SSD

and
Dell M4600 Precision ( also i7 quad-core, nvidia quadro 2000M, SSD)

both are UEFI computers.

Anyone figure this one out yet?

---

### Post by darkod on 2012-05-20
Does the installer freeze immediately or at the end when trying the grub install?

---

### Post by darkod on 2012-05-20
As far as I have seen here, the EFI dual boot is a bit complicated right now. I guess still not mature enough. Windows bootloader and grub2 clash.

Maybe you'll find some ideas here:
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)

Also note that I have seen recommendations to backup the windows files from the EFI partition before you install ubuntu, because often it can delete them. You would need to copy them and put them back later.

If possible, I would consider sticking with the bios boot. EFI is still too new and with issues when dual booting.

---

### Post by abstractAlchemist on 2012-05-24
Sorry for the long delay in response.

It freezes right after hitting the first screen ( after selecting install ubuntu, or the desktop freezes when using the try ubuntu without install option ).

I don't see the issue;  it works perfectly fine in 11.10 ( UEFI, that is ).  Is it a kernel issue?

I haven't had the same experience with ubuntu UEFI install deleting windows install bootmanager;  they seem to work just fine to me except for the fact that grub-efi can't see the windows boot loader.  Fortunately, dell and asus have really good looking boot loaders for their UEFI hardware, so i don't have any issues.

---

