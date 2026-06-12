---
title: "Problems Booting to GRUB on Windows 8 Laptop - Newb"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by renegaderats on 2013-06-24
These are the exact steps I took when installing ubuntu 12.10x64 on my win8x64 machine (hp envy dv7-7233nr - currently stock hardware).
[http://www.avoiderrors.net/dual-boot-windows-8-and-ubuntu-12-10/](http://www.avoiderrors.net/dual-boot-windows-8-and-ubuntu-12-10/)
(I am not affiliated in anyway with this site)

I have Ubuntu successfully installed and am actually posting this from inside of it right now HOWEVER the problem is that my machine doesnt want to boot to GRUB and alow me to choose my boot partition, instead it goes straight to windows 8! In order to get into ubuntu I actually have to pull up my BIOS's boot manager and select the correct partition from there... also woth noting is that in this list there are 2 ubuntu listings (one with an uppercase U and the other with a lower case) the upper case listing actually takes me straight into windows 8!? while the lower case takes me into GRUB (where I'm trying to boot to).

I know that EFI/UEFI plays a role but to be honest I dont even know what they do/are. I also heard that "secure boot" may be an issue but it doesnt seem like thats something I should turn off (enable/dissable option in BIOS).

If anyone can advise a new linux convert I would be extremely greatfull as I'm trying to make Ubuntu my primary OS, only using windows in a Vbox to access exe files, adobe softwares, and whatever else we still rely on Bill Gates for.

Thanks again for any advice offered!

---

### Post by oldfred on 2013-06-24
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

