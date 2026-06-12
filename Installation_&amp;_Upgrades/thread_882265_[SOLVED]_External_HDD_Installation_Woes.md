---
title: "[SOLVED] External HDD Installation Woes"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by EdgeWalker on 2008-08-06
I have been trying for several hours to install 8.04 to an external USB hard drive using the following instructions:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/]("http://www.pendrivelinux.com/...")

I followed the instructions exactly the 1st time (it instructs you to physically remove all other hard drives.) When finished, I got Grub error 2, with or without the internal hard drive attached.

A few tries later, I didn't detach the internal drive (why would you really do that, unless you're not confident that you can identify the drives in the install menu :rolleyes:)  This time the Grub menu does appear :) but alas, none of the options work.

Attempting to boot to Ubuntu results in:
Error 17 Cannot mount selected partition

Attempting to boot to Windows results in:
Error 13 Invalid or unsupported executable format

I've searched elsewhere, but so far I haven't seen this situation.  Thanks in advance. 

*EDIT:*
**Contents of menu.lst (after comments only)**
> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d5e044e1-3ad5-4765-a53c-53273feb9917 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d5e044e1-3ad5-4765-a53c-53273feb9917 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
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
chainloader	+1



**Results of fdisk -l**
> (this is the internal drive)
Disk /dev/sda: 320.0 GB, 320072933376 bytes
Disk identifier: 0x07220721
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

(this is the external drive)
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
Disk identifier: 0x00058b02
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38156   306488038+  83  Linux
/dev/sdb2           38157       38913     6080602+  82  Linux swap / Solaris


**Contents of device.map:**
> (hd0)	/dev/sda
(hd1)	/dev/sdb

---

### Post by Pumalite on 2008-08-06
Check this thread:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by trebllaw on 2008-08-07
try changing (hd1,0) to (hd0,0) on your menu.lst, that worked for me.. also, change bios settings to boot from usb device first.. (this is assuming you installed GRUB on the MBR of your external hard drive).. let me know if it worked for you

---

### Post by EdgeWalker on 2008-08-07
> **Pumalite said:**
> Check this thread:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

Thanks for the link, but unfortunately that thread uses the exact link I mentioned in my post, so no new info there.  I also skimmed every entry in the thread (just 5 pages), but it doesn't look like my problem is covered there. :-?

---

### Post by EdgeWalker on 2008-08-07
> **trebllaw said:**
> try changing (hd1,0) to (hd0,0) on your menu.lst, that worked for me.. also, change bios settings to boot from usb device first.. (this is assuming you installed GRUB on the MBR of your external hard drive).. let me know if it worked for you

The BIOS is definitely set to USB-HDD first.

Edit: Yes, Grub is on the ext. hdd.  If I remove the drive, the PC goes back to behaving exactly as it did before I started this project, and boots happily into WinXP Pro.

---

### Post by EdgeWalker on 2008-08-07
Incidentally, I have also tried plugging the hard drive into a few other of the PCs in the office and booting, always with the same result.

Error 17 for linux
Error 13 for Windows

---

### Post by EdgeWalker on 2008-08-07
> **trebllaw said:**
> try changing (hd1,0) to (hd0,0) on your menu.lst, that worked for me.. also, change bios settings to boot from usb device first.. (this is assuming you installed GRUB on the MBR of your external hard drive).. let me know if it worked for you

Swapping (hd1,0) and (hd0,0) in the menu.lst file solved the problem.

I'm a bit confused as to WHY this worked.  I guess it was hard to notice since I had the misfortune of having internal and external drives of the exact same size and company :)

Thanks for the help!

---

