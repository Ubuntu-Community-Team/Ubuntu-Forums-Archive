---
title: "Grub problem - booting Zeta, Ubuntu and Windows"
date: 2005-08-24
forum: Installation &amp; Upgrades
---

### Post by ChristOff on 2005-08-24
Hello,

I recently installed Zeta (the "new" BeOS). As you maybe know, it comes with a handy boot manager called bootman. After the installation, I chose to use bootman as my OS selector. This setup works flawlessly for booting BeOS and Windows, but I can't boot into Ubuntu (hoary) anymore. 

For what I understand, I'd have to install Grub into my Ubuntu partition and not in the MBR anymore (as bootman lies there). OK, but I don't know how to do that. Every documentation I come accross explains how to install grub in MBR, merely mentionning it's installable in another way and never explains how to do that. If I boot from a LiveCD and sudo grub-install (hd1,0) will that do what I want? I read some warning about using grub-install (about device.map; system unbootable, etc), thus I prefer being sure before trying anything.

FYI my partitions are:
First disk primary: Windows
First disk extended with: WinProg, Misc1, Zeta
Second disk primary: Ubuntu
Second disk extended with: UbuntuSwap, WinSwap, WinTemp, Misc2

Thanks in advance for answering,
ChristOff

---

### Post by ajm2005 on 2006-12-16
Don't install the Zeta bootloader!! The Zeta boot manager is unable to boot linux...

You're better off using the grub boot loader, which can load linux/ windows, and can also boot into Zeta. Assuming Grub is already set up to boot your linux and windows partitions, you should install Zeta without installing it's boot manager, and then add a few lines to your GRUB menu configuration (/boot/grub/menu.lst) to allow Grub to boot Zeta / BeOS.

You need to use the "rootnoverify" command (which prevents grub from trying to mount the zeta file system - grub doesn't understand the zeta file system), and then the chainloader command which will look at the first sector of your zeta partition and attempt to boot whatever is there (i.e., Zeta). 

The only tricky part is specifying the appropriate drive/ partion for zeta in the rootnoverify command. grub has its own naming conventions for drives and partitions which are a bit different than the linux/  ubuntu naming conventions. If Zeta is on your first drive (specified by grub as hd0) in the 4th primary partiton (specified by grub as 3), then you would add the following entry to /boot/grub/menu.lst 

(put this in the appropriate section in menu.lst)

[B]title ZETA OS
 rootnoverify (hd0,3)
 chainloader +1
 boot
[/B]

You will then be able to select zeta from the grub menu when you are booting the machine.

So basically I would install Windows first, then ubuntu (with the grub bootloader), and then you can install Zeta (but do not install Zeta's boot loader). Then boot into ubuntu and modify grub's menu.lst config file, to add Zeta as a boot option.

more info on specifying grub boot options:
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

---

