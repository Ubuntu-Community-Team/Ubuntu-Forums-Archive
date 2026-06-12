---
title: "Install Ubuntu in USB Drive?"
date: 2016-10-25
forum: Installation &amp; Upgrades
---

### Post by gangart20 on 2016-10-25
Hello community!

So I was trying to use Ubuntu from my USB Stick as a standalone boot, which works fine as Live Ubuntu. So I am choosing the USB drive to boot in the BIOS and I am using Ubuntu straight from the stick (I guess?), but just they "try before installing" version. Now, there is the "install" icon on the desktop - does this installing mean that it will install it straight onto the USB Stick, or it will install it on my main computer partition?

All the best

---

### Post by oldfred on 2016-10-25
Install is to another device, either internal or external.
And if newer system, how you boot install media UEFI or BIOS is then how it installs. Older systems with BIOS of course only boot & install in BIOS mode.

---

### Post by gangart20 on 2016-10-25
So, I used the Universal USB Installer to play the .iso on the USB Drive and formatted it in the process of it (and put some space aside for private usage). 

Is it possible now that if I choose to use the install option from the Live Ubuntu Desktop it will install it to the USB Drive in any way?

---

### Post by oldfred on 2016-10-25
Not to same flash drive without major effort.
Use a small flash drive for the installer and a larger flash drive or external drive as install to location.

Is system UEFI or BIOS?
Either way install must use Something Else install option.
Best to create partitions in advance and if BIOS you can use MBR or gpt, but if UEFI, you must use gpt.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by sudodus on 2016-10-25
The following link will add some confusion ;-) I mean it will offer a third alternative, a persistent live drive. And it is a good idea to install Ubuntu or maybe a lighter flavour, Lubuntu, Ubuntu MATE or Xubuntu as an installed system in a fast USB 3 drive.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

