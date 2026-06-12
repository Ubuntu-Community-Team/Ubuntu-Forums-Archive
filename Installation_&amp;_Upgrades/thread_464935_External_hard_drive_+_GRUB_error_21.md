---
title: "External hard drive + GRUB error 21"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by Mal1024 on 2007-06-05
I just installed Ubuntu on an external hard drive. When attempting to boot, it shows the following:

Loading GRUB stage 1.5....

GRUB loading, please wait...
Error 21

Then nothing happens. I have looked up Error 21 and it is something like "Drive does not exist". There is an option in the BIOS setup called USB SCSI SubClass suppport that may be the solution, but there is apparently a possibility of the system hanging during POST if this is enabled.

Should I just enable this option or is there another solution?

---

### Post by jackiecanev2 on 2007-06-05
could you post your output from 'sudo fdisk -lu', along with a copy of the bottom part of your /boot/grub/menu.lst file?

---

### Post by Mal1024 on 2007-06-05
> **jackiecanev2 said:**
> could you post your output from 'sudo fdisk -lu', along with a copy of the bottom part of your /boot/grub/menu.lst file?


-----------------------------fdisk -lu----------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78140159    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    74846834    37423386   83  Linux
/dev/sdb2        74846835    78140159     1646662+   5  Extended
/dev/sdb5        74846898    78140159     1646631   82  Linux swap / Solaris

-------------------------------------menu.lst---------------------------------------------

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=414d9c6f-8039-4ffe-858c-a22ce1d95215 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=414d9c6f-8039-4ffe-858c-a22ce1d95215 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
-------------------------------------------------------------------------------------------

---

### Post by jackiecanev2 on 2007-06-05
check out your BIOS. See that you can make it boot from usb port, configure your port and remember to connect the Drive in the specific port always.

---

### Post by Mal1024 on 2007-06-05
Thanks very much - it's done it!! :D

---

### Post by igtech on 2007-06-09
I have the same problem...
ap
OK Yes, BUT....

Then I need to have this external HDD  always plugged into my computer? I made this on my laptop and a "huge" external HDD, now I want to keep carrying only y laptop with just Windows XP. Then I Cannot??? 

Thanks for any suggestion!

---

### Post by joe1-1 on 2008-03-07
Running Ubuntu 7.10 on my laptop and had the same issue when trying to install Untangle to an external HD. It moved my GRUB install to the external HD. My fix:

- Had both hard drives connected
- Booted off the Ubuntu CD
- Opened a terminal window
- Ran sudo nautilus
- Opened the device.map file in the /boot/grub directory on the external HD and found it had changed my laptop HD from hd0 to hd1
- Opened the menu.lst file on my laptop HD and copied the first menu option
- Opened the menu.lst file on the external HD and pasted the menu option from my laptop HD
- I changed the pasted menu option to point to hd1 instead of hd0
- Rebooted off the external HD, chose the menu option to boot off my laptop HD
- Once booted I opened a terminal window
- Ran fdisk -l to verify my boot disk which was sda
- Ran grub-install /dev/sda which reinstalled grub on my laptop HD
- Disconnected the external HD and rebooted, everything was fixed

---

