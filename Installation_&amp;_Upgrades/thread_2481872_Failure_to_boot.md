---
title: "Failure to boot"
date: 2022-12-11
forum: Installation &amp; Upgrades
---

### Post by mws3b on 2022-12-11
I have decided to use an old Toshiba Satellite laptop completely as an ubuntu however after install is complete and the system asks to restart then followed by “please remove usb boot device and press enter” The PC then fails to boot. I tried many times and even tried reinstalling ubuntu on a partition using the boot device installer leaving me with two ubuntus on my pc but none of them boot. After using “try ubuntu” and installing “boot repair” I was given a link to share which is:
[https://paste.ubuntu.com/p/QBSHNRbTfT](https://paste.ubuntu.com/p/QBSHNRbTfT)

Additionally my PCs BIOS menu does not include the ability to shift from BIOS LEGACY
Toshiba Satellite L550
Core i3(don’t know which generation)
4GB RAM and 320 GB memory. 
AMD RADEON

---

### Post by oldfred on 2022-12-11
See line 293.

It looks like you have installed more than once, but in different boot modes. And have two installs sda3 & sda4?
How you boot install media, UEFI or BIOS is then how it installs.
You have grub in gpt's protective MBR and bios_grub partition for BIOS boot and an ESP - efi system partition for UEFI boot.
Since fstab now shows the mount of the ESP, I expect last install was in UEFI boot mode.

You have to then have UEFI settings set to default boot in mode you chose to install.
With Toshiba I think it is f2 to get into UEFI/BIOS settings. You need to turn off BIOS/Legacy/CSM boot mode and/or turn on UEFI boot mode.

I was able to install Kubuntu on my 2006 laptop with only 1.5GB of RAM. I did not expect it to work as Ubuntu would not install in that little amount of RAM. 
Older systems often work better with lightweight flavors. Yours should be ok with 4GB, but may be bit better with Kubuntu as mid-weight or one of the light weight flavors.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://opensource.com/article/20/5/linux-desktops](https://opensource.com/article/20/5/linux-desktops)
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by mws3b on 2022-12-12
I have tried BIOS menu on Toshiba. However through comparison with Toshiba tutorials on youtube it appears my particular models MIOS model doesn’t include the ability to switch between BIOS LEGACY and UEFI. I personally checked and found that it doesn’t.

---

### Post by tea for one on 2022-12-12
I've noticed a few threads recently, where some old Legacy Bios PCs have boot problems after Ubuntu installation.

You could try this:-
Boot into a live session in legacy mode.
Open Gparted and create a msdos partition table.
Then make _one_ Ext4 partition.
Open the installer and install to your previously created partition.
(i.e. do not let the installer "Erase Disk and Install")
If you see a message/warning about ESP missing, ignore it and continue the installation.

It may work, it may not................?

Finally, given the age of your PC, perhaps Lubuntu or Xubuntu may be worth a shot.
(Lubuntu uses a different installer)

---

