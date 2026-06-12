---
title: "Newbie-Netbook won't boot after upgrade"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by oldbill1969 on 2010-08-16
Hi all, total newbie to ububtu which I have been using with dual boot on my netbook. All has been well until I went through the upgrade process from 9.10 to 10.04.
After going through the process the netbook restarted went past the splash screen and displayed the message
error: no such device:a0c6fc38-13ae-4af3-8fde-0a7e16bb6637
grub rescue>

I cant even go through the recovery options on the splash screen it just reverts to the above message.
Can anyone help please?

---

### Post by Herman on 2010-08-16
You just need to boot into it and install updates. But ironically, since you can't boot, you can't get the updates that will fix your booting problem.

Unless ...

Unless you have made yourself another Ubuntu installation in a USB that has GRUB2 in it and/or you know how to boot from Gnu/Grub's CLI. 
OR, you know how to chroot into your installation from a Live CD or Ubuntu in a USB or something like that and get the updates that way.

Don't worry, here are a couple of links that should help you, pick whichever one seems easier for you, 

[GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  NEW!  Rescue your System   

[COLOR=#333333][How to chroot]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#chroot") - [/COLOR]use a Live CD or another Ubuntu installed in a hard disk or USB to fix  your GRUB

After you chroot into it or boot it, whichever you decide to do, make sure you run sudo apt-get update and after that run sudo apt-get upgrade.
if you want to make sure, run sudo grub-mkconfig -o /boot/grub/grub.cfg as well.

Regards, Herman :D

Oh I forgot to mention, it's easy if you have a full Ubuntu installation in a USB, just boot the USB's Ubuntu, and run sudo grub-mkconfig -o /boot/grub/grub.cfg with it plugged in to the netbook with the unbootable operating system. 
Hopefully the USB Ubuntu installation's GRUB2 will detect the netbook's Ubuntu and add it automatically to the boot menu for you. 
With most computers it should detect the internal operating system(s), but sometimes it doesn;t, I don't know why, something to do with the BIOS in some computers probably. 
Assuming it works, just reboot and choose the netbook's Ubuntu from the boot menu in the USB's GRUB2.
Then apt-get update and apt-get upgrade.

---

