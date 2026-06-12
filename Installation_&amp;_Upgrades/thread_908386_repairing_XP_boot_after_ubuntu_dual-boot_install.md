---
title: "repairing XP boot after ubuntu dual-boot install?"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by wamanning on 2008-09-02
[FONT="Arial"]i have a problem w/ XP no longer booting from GRUB after a successful dual boot install of ubuntu 8.04.

i think it's the exact same problem as in this thread, but i never saw (nor found) a solution to fix the XP booting.

[http://ubuntuforums.org/showthread.php?t=424627](http://ubuntuforums.org/showthread.php?t=424627)

booting to the ubuntu partition is fine, booting to the XP Recovery partition is fine, but booting to XP itself in between those partitions hangs.  

it never gets to the XP splash, just the single line of text from GRUB saying it's loading something...

here's the contents of menu.lst:[/FONT]

[FONT="Courier New"]## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aaa6cede-19ca-4ce0-ac46-ee09f17654e9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aaa6cede-19ca-4ce0-ac46-ee09f17654e9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		HP Windows XP System Recovery
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/FONT]

and here is the contents of fdisk -l:

[FONT="Courier New"]Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9078    72919003+   7  HPFS/NTFS
/dev/sda2           13638       14593     7673400    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            9079       13637    36620167+   5  Extended
/dev/sda5            9079       13450    35118058+  83  Linux
/dev/sda6           13451       13637     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order
[/FONT]

i'm pretty much an ubuntu noob, so i'm having trouble discerning any real trouble here much less how to fix it.  since it hangs after i select XP from the grub menu, and says it's doing something, i assume it's a problem w/ the XP boot code.

---

### Post by Pumalite on 2008-09-02
You seem to have a Partition Table problem
Take a look with rescuecd and try to fix it:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by wamanning on 2008-09-02
> **Pumalite said:**
> You seem to have a Partition Table problem
Take a look with rescuecd and try to fix it:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

yehp, just figgered it out.  used the testdisk utility, which is on the rescuecd image and can be downloaded via synaptics, to rebuild the boot sector.

everything boots up just fine now!

---

### Post by gurlinux on 2008-09-03
> **Pumalite said:**
> You seem to have a Partition Table problem
Take a look with rescuecd and try to fix it:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

Hi there, exactly the same problem here. 
My question: did you pinpoint the Partition Table problem due to the message "Partition 2 does not end on cylinder boundary" contained in the fdisk output?

If so, as I have the same message, I'll try the rescue CD as a last resort before trying to repair WinXP (and possibly losing all installed programs...)
Thanks!

---

### Post by gurlinux on 2008-09-04
Just an update, for the record: the problem was the NTFS boot sector on the WinXP partition (which had been shrunk as part of the Kubuntu installation). 
Had to rebuild the NTFS boot sectors (both the original and backup) with TestDisk (so thanks for the tip on SystemRescueCD) and then WinXP came back to life!
At first WinXP went into chkdsk (it apparently detected that "something" happened) and then booted up just fine.
Thanks again

---

### Post by Pumalite on 2008-09-04
You are welcome. Good luck!

---

