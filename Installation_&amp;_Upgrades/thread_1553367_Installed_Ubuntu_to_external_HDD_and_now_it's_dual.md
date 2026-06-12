---
title: "Installed Ubuntu to external HDD and now it's dual boot"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by LuiePL on 2010-08-14
I installed Ubuntu to an external hard drive and I wanted it to be a portable OS I could take with me and still maintain my settings and files and what not. My problem now is, I cannot boot into Windows without having the USB drive connected. I also cannot boot directly to the drive by selecting the USB drive from my boot options on start up, I have to let it go into the boot menu.

So I need help with being able to boot directly from the USB drive on any computer, and being able to boot into Windows without having the USB drive plugged in. Hopefully this can be done without re-installing Windows. Thanks.

---

### Post by sikander3786 on 2010-08-15
Hi.

You need to fixmbr for the Windows Install and that will require a Windows CD. Have you got one?

For the second part of booting Ubuntu off a USB drive, you can create a startup disk using the Startup Tool in the System menu of Ubuntu or [Unetbootin]("http://unetbootin.sourceforge.net"). I recommend using Unetbootin because it will ease up the whole process a bit.

Edit: I am not sure though that it will save your settings or not. Never tried it.

---

### Post by oldfred on 2010-08-15
Common problem. When you install to a second (internal or external drive) you need to use the advanced button to choose where to install grub. Install a windows boot loader to the internal and grub to the external. Instructions:

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by LuiePL on 2010-08-16
> **sikander3786 said:**
> Hi.

You need to fixmbr for the Windows Install and that will require a Windows CD. Have you got one?

For the second part of booting Ubuntu off a USB drive, you can create a startup disk using the Startup Tool in the System menu of Ubuntu or [Unetbootin]("http://unetbootin.sourceforge.net"). I recommend using Unetbootin because it will ease up the whole process a bit.

Edit: I am not sure though that it will save your settings or not. Never tried it.

I did the fixmbr and got that working (Thank you!)

I used unetbootin on the external hard drive, and booted to it, but I'm just getting a blinking cursor.

---

### Post by oldfred on 2010-08-16
Unetbootin is for making bootable flash drives. If you have a full install you have to reinstall grub2. If you used unetbootin to install to your usb drive you may have overwritten your install.

See previous post or :

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

