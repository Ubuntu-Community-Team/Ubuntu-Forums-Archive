---
title: "[SOLVED] GRUB boots from wrong disk"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by goofygutt on 2008-11-20
I've got a Acer Aspire One, and wanted to install Ubuntu on it, and I already had Mandriva installed on a memory stick that boots nice and easy on the Aspire. And then, to install Ubuntu on my CD-Rom-free laptop, I downloaded the UNetBootIn for Ubuntu 8.04 on this site: [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

It installed Unetbootin to my GRUB so that I could start downloading and installing Ubuntu trough the net. 

During installation, I choose to install to the SDD on the laptop and not the memorystick of course. And when the installation finished, I forgot to pull out the memorystick, and Ubuntu booted just fine, but since I wanted to use my pc without any memorystick to boot it up, I rebooted the pc without the memorystick in it and I got the error "Error 21: The selected disk does not exist" 

So it kinda seems that Ubuntu is installed to the SDD on the laptop, but it needs to use GRUB bootloader from the memorystick or something to boot it up, guess I've mixed it all up somewhere along the way.
Any way to fix it? Or how do I install Ubuntu properly to my c-rom-free laptop?

---

### Post by caljohnsmith on 2008-11-20
How about going ahead and booting into Ubuntu, open a terminal (Applications > Accessories > Terminal) and post:
```
sudo fdisk -lu
```
And please identify your partitions; we can work from there if you want.

---

### Post by dstew on 2008-11-20
When you installed grub, it counted all the disks that were present, and perhaps since the memory stick was in there, the hard disk came out as number two. So, when grub was installed, I bet that (hd1,0) was set as grub's root. But, when you pull out the stick, the hard disk is now disk 1, so grub's root should be (hd0,0).

I assume when you boot without the memory stick, you get the grub menu, and the error when you select Ubuntu, is that right? If so, you can change the grub root on the fly like this:

Instead of pressing 'enter at the grub menu, press 'e'. That will get you into a mode that lets you temporarily edit the menu commands. Use the arrows to move to the root statement, and press 'e' again. This will let you edit the line. If it says root (hd1,0) change it to (hd0,0). Then press 'enter', followed by 'b' to boot.

If changing the root argument this way fixes it, you can make it permanent by editing /boot/grub/menu.lst. However, if you plug in a memory stick at boot time, it will not work again most likely, for the same reason. Grub depends on how your BIOS enumerates the disks, and some BIOSes will change the enumeration depending on how many disks are there, and the boot order.

---

### Post by goofygutt on 2008-11-20
thanks! After editing the GRUB list it boots just fine, thanks alot :)

---

