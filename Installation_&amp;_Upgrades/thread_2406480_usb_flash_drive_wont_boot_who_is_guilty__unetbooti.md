---
title: "usb flash drive wont boot: who is guilty?  unetbootin or my iso files?"
date: 2018-11-21
forum: Installation &amp; Upgrades
---

### Post by sirdeseagull on 2018-11-21
i have been trying to create a bootable usb drive with all sort of distro's and even windows, but upon rebooting it does nothing...
it boot my current distro(elementary os) as if my usb dont exist.  i dont understand, i have done this before using unetbootin and everything used to work fine.  
any idea what i am doing wrong?  or is there any other alternative to create a bootable usb??

---

### Post by Tadaen_Sylvermane on 2018-11-21
I use the dd command, but it's dangerous. It has zero sanity checking, runs as root, and does exactly what you tell it. Easy to trash your whole system if you don't do it right. I don't know if this is actually accurate regarding the real name. Some say DD is Disk Destroyer. I've never had success with Unetbootin before, not a single one.

I think this is right, haven't used it in awhile. /dev/sd? should reflect the device your flash drive is on. Use the main device aka /dev/sda, or /dev/sdb, not the partitition aka /dev/sdb1 or whatever. Use at your own risk though. If you get it wrong, you are screwed.

```
dd if=/path/to/iso of=/dev/sd? bs=4096
```

---

### Post by ajgreeny on 2018-11-21
Safer then using dd direct in the terminal is [mkusb]("https://help.ubuntu.com/community/mkusb") which has always worked very well for me and many other Ubuntu users.

However, there should be a keyboard keypress that shows you a device boot-priority menu so have a good search through your computer manual, or search online for the key to press for that menu, and you may then find that the USB is already good to go.

---

### Post by kurt18947 on 2018-11-21
There is a function in the gnome app "Disks" or gnome-disks. Launch the app and click on the hamburger menu. One option should be 'restore disk image'. Select your source and destination. I've had good luck using that to create a live USB. It will only create a bootable USB, won't help with adding persistent storage or any of the other fancy stuff.

---

### Post by C.S.Cameron on 2018-11-21
UNetbootin (Linux) has been working a little dodgy with 18.04, if at all.
I prefer mkusb (Linux). It works both BIOS and UEFI.
YUMI (Windows) should work fine with BIOS boot and works with multiple ISO's

---

### Post by oldfred on 2018-11-21
If UEFI secure boot is on, you have to turn on allow USB boot. USB booting is not considered secure, so you have to explicitly allow it. Since setting is there, you may have to turn it on, even if UEFI boot. Normally BIOS/CSM/Legacy  has fewer restrictions as mention to be backwards compatible with very old systems.

---

