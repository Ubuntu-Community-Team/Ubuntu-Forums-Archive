---
title: "How I installed 6.10 to External USB Drive"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by leobaby on 2007-04-11
*(I am posting this in a new thread because I believe it may be helpful to someone.)*

Here is how I performed an **install of 6.10-desktop to an external usb hard drive (2.5")** and the issues I faced. Whether it's too detailed or not enough it should help someone. 

The computer is a dell laptop. I do not want to modify the internal drive at all; and I am able to choose to boot from another drive.

Before boot, my computer allows me to F12 and select boot device, usb is in the list.
If this is not possible, you might need to create a grub boot cd, or possibly in your bios you need to choose which usb drive when usb is selected. 

Small issue, my 2.5" external disk does not spin up when plugged in before turning on the computer.

**The install**:

[LIST]
[*]**prepared the target drive**. Ubuntu is unhappy to install when theres stuff on this drive it wants to mount, so I deleted all the partitions in windows Disk Management.
[*]**booted from the Ubuntu CD**.
[*]Once at the desktop, I did not see usbdisk icon on the desktop. Good for me.
[*]**started the install** and proceded with the **usual options**.
[*]At the ***Select a disk***  I chose the second drive, my usb drive, sdb.
[*]At the ***Prepare disk space***  I chose 'Manually edit partition table'. 
[*]At the ***Prepare partitions***  I made sure to choose the empty drive and created pri 16384MiB ext3, and ext 2048MiB swap.
[*]At the ***Ready to install*** dialog, I changed the 'GRUB will be installed to' option to (hd1), putting grub on the external usb. This is important, also I did not want to modify my internal drive with a boot sector. 
[*]After rebooting, I choose to **boot from the external usb drive**. Since I am booting from the drive it now appears as hd0 instead of hd1.
[*]Grub loads, so it is booting off the correct drive, but **Error 17:** Cannot mount selected partition. Press something, then presented with the grub boot menu, choose e to edit the first option, then e to edit line root (hd1,0) and changed to root (hd0,0). Then pressed b to boot 
[*]and **success**. Once at the desktop, terminal sudo **gedit /boot/grub/menu.lst**
and copied the first group of options to the very top and did the same changing **(hd1,0) to (hd0,0)**
[/LIST]
 
If you can't boot and need to edit your menu.lst, you can boot with the 6.10 disc, which will mount the usb disk, and from terminal
sudo gedit /media/usbdisk/boot/grub/menu.lst

This is much better than the days of mkinitramfs, but not quite perfect.

---

### Post by confused57 on 2007-04-11
Nice howto, thanks for sharing.

You also need to change the line with groot to (hd0,0), or a kernel update will change everything back to (hd1,0):

[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

