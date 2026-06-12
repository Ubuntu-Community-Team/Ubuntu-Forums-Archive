---
title: "Bootloader lost entry after installing to external USB drive"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by blackmath on 2010-06-04
A subtle one this:

I had a perfectly working dual-boot windows/Ubuntu setup on my laptop. Today I decided to install Ubuntu on an external USB drive for testing purposes (a safety measure, I thought). I booted my laptop using a USB stick (the one I originally installed my dual-boot setup from) and installed Ubuntu onto my external USB drive, rebooted and all was well - I had a safe experimental installation on my external USB drive. But oh dear - I didn't predict that the bootloader on my laptop's hard drive would of course have been replaced and an entry put in for my external drive! So now my old dual-boot partitions are still there on my laptop's drive, but the bootloader has no knowledge of them. 

How can I restore things to how they were ?

---

### Post by Herman on 2010-06-04
:) You could try booting into your USB Ubuntu, since that's the easiest, and running 'sudo grub-mkconfig -o /boot/grub/grub.cfg', to see if it will detect your operating systems in your computer's internal disks and automatically add them to the boot menu.
> sudo grub-mkconfig -o /boot/grub/grub.cfgThen you could reboot and boot into your internal Ubuntu and restore your internal GRUB to MBR. That would be the easiest way if it will work.

I have found that most of the time USB installed Ubuntu operating systems can automatically add internal OSes to the boot menu and actually it's a good way to rescue internal OSes with boot loader problems.
In some computers it might not work though, (depending on the BIOS I imagine).

If your USB external Ubuntu's GRUB can't detect your internal drive's operating systems then there are lots of other solutions you can use.
Another way is this, [How  To Re-install GRUB2 from a Ubuntu Live CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD") - without the need to  chroot.
You could use your USB Ubuntu to do that from, it doesn't need to be done from a Live CD, just some other Ubuntu operating system.
You should install your internal Ubuntu's GRUB to MBR in the internal disk and your USB's GRUB to MBR in your USB external disk.

If you're not sure and you would like extra help, please post the output from 'sudo fdisk -lu' here and I or somebody else here should be able to help you more.

---

### Post by John Bean on 2010-06-04
Although it's about GRUB2 recovery after installing Windows this walkthrough is equally applicable to your situation:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by wilee-nilee on 2010-06-04
I have found when doing a full install to another external like a thumb, that the default grub install is to the mbr of the on board HD, so you have to click on the advanced button in the last install window to make sure grub goes to the correct mbr.

---

### Post by kansasnoob on 2010-06-04
If you require detailed help please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

