---
title: "[SOLVED] Configuring grub menu for the installation of ubuntu in a usb hard disk"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by adam98 on 2008-10-28
Hello all,

I have been experimenting with ubuntu in a vm and i have decided to install it in a external hard drive. So i have done the following:
*partitioned the hard drive and created a ext3 partition ( sdb5 )  and a swap one (sdb6).
* installed ubuntu in the ext3 partition.
* intalled grub in the external disk ( sdb) so i can boot from the internal disk when the usb cable of the disk is disconnected.
* configured BIOS to boot first from the usb drive and then from the internal hard drive ( /dev/sda1 which contains a windows xp OS).

Now when i boot with the external disk connected grub runs correctly but when i select the ubuntu os to run it displays an error message "error 22 cannot find the partition" ( or something like that :) )
Now i understand that this is a problem in the /dev/.../menu/lst of grub. But i cannot do the corrections myself, even though i have read some relevant post in the forum :( . The relevant entries in the file are the following:


title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            **(hd1,4)**
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=212a8d0f-df92-4ced-bd$
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            **(hd1,4)**
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=212a8d0f-df92-4ced-bd$

title           Ubuntu 8.04, memtest86+
root            **(hd1,4)**
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP (loader)
root            **(hd0,0)**
savedefault
chainloader     +1

I know that i have to change the root values in the configuration file but i don't know how.

p.s. I also read in the forum that one solution is to disable the internal hard disk from the BIOS and then install ubuntu but this option is not available to my BIOS and moreover i would like to correct the configuration file.

---

### Post by caljohnsmith on 2008-10-28
All you should need to do is change all the Ubuntu entries to use (hd0,4) instead of (hd1,4); the reason why is on start up, Grub sees the order of drives as the BIOS boot order, not as how the drives are ordered in Ubuntu's /dev directory. So if you boot off the USB drive, it will be (hd0) on start up, even though it is probably /dev/sdb when you are in Ubuntu. Also, you'll need to use Grub's mapping technique to boot your Windows XP, because Windows XP won't boot off of anything except the first boot drive, unless you change the boot.ini file:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Give that a shot and let me know how it goes. :)

---

### Post by adam98 on 2008-10-28
It worked!I just boot to ubuntu correctly!Thank you for your help :)
One last question, the mappings you propose are for the xp operating system WHEN the usb cable is connected and must be done in the same file (menu.lst) in the end ,in the section about the other OS's, right? Thanks again

---

### Post by caljohnsmith on 2008-10-28
> **adam98 said:**
> It worked!I just boot to ubuntu correctly!Thank you for your help :)
One last question, the mappings you propose are for the xp operating system WHEN the usb cable is connected and must be done in the same file (menu.lst) in the end ,in the section about the other OS's, right? Thanks again
Yes, just add that Windows entry I gave to the end of the menu.lst file after the "Other Operating Systems" heading. And to edit your menu.lst on the USB drive, you certainly would need to have the USB drive hooked up via its cable so you can access it, if that's what you're asking. :)

---

### Post by adam98 on 2008-10-28
NO! I meant that i guessed that you add these entries in order for xp to run WHEN the usb is connected, because if it is not the bootloader of windows runs so there is no problem!! You answeared all my guestions anyway and i am so greatful for this!Thanks again :)

---

