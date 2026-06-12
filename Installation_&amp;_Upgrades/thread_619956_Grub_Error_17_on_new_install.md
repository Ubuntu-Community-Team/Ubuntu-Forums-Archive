---
title: "Grub Error 17 on new install"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by bettik on 2007-11-22
Hi,

Thought i'd give Ubuntu a spin. Install went well right up to the first boot from the hard disk.  Configuration is single hard drive. Ntfs primary resized during install to accommodate Ubuntu. I pretty much let the installation program make all the decisions. Now I can't boot into XP or Linux. Disk is as follows.

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41034102

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       15719   126262836    7  HPFS/NTFS
/dev/hda2   *       15720       19297    28740285   83  Linux
/dev/hda3           19298       19457     1285200    5  Extended
/dev/hda5           19298       19457     1285168+  82  Linux swap / Solaris

I've tried to research solutions but I'm afraid I don't understand them (or even if they are applicable to my particular problem). Also here is a listing of what i think is the pertinent parts of menu.lst

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7392ccfa-89d6-47f6-a14f-b6d51859c4f8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7392ccfa-89d6-47f6-a14f-b6d51859c4f8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Please help if you can. thanks

---

### Post by banewman on 2007-11-22
This link [http://justlinux.com/forum/showpost.php?p=869980&postcount=6](http://justlinux.com/forum/showpost.php?p=869980&postcount=6) gives a good explanation - the solution is for another comp but follow it with your own parameters and you should be fine. :)

---

### Post by bettik on 2007-11-23
> **banewman said:**
> This link [http://justlinux.com/forum/showpost.php?p=869980&postcount=6](http://justlinux.com/forum/showpost.php?p=869980&postcount=6) gives a good explanation - the solution is for another comp but follow it with your own parameters and you should be fine. :)

Thanks. I tried this and everything else I could find regarding the issue to no avail. Got new Grub errors. I spent the last 2 days trying to recover from the Ubuntu install and just finished. I do appreciate your response though. I'll have to try again when I have built a new system (project for the end of the year) as I suspect that issue is due to a very old MB/BIOS.

---

