---
title: "Grub Editing"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by Atbash on 2012-10-16
I own a HP Folio 13 and have the "screen goes black" bug when I try to install Ubuntu (the kernel runs and then the screen blacks out).  I've noticed many sites suggest adding "acpi_backlight=vendor" to the kernel.

I'm wondering if anyone can explain how I can go about adding this to the kernel from Windows 7.  :confused:  I'm a newb, so please be gentle.  

Thanks for your help.

---

### Post by oldfred on 2012-10-16
Welcome to the forums.

You cannot use Windows to do anything in Linux as it does not recognize any Linux formats, only its NTFS or FAT.

You can edit things from a liveCD or USB, but if just a kernel edit on booting you can manually edit boot parameters from the grub menu.

Often screen going off needs nomodeset, but sometimes other boot options or several combined.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Just press e on grub menu and edit linux line. Normally replacing splash quiet entries. Each time you boot you need that but it gives a way to test different parameters. Once you determine your parameters you can make them permanent by editing /etc/default/grub file.

---

