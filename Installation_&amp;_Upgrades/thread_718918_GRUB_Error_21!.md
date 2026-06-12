---
title: "GRUB Error 21!"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by markekeller on 2008-03-08
Hello folks,

I have an older dual-drive system, both of whose disks recently died.  So I installed a newer IDE disk, and put Windows XP on it (in the BIOS, it thinks the drive is slave, for some reason, even though the jumpers are set to master - but it works fine).  Then I installed a SATA controller card and installed a SATA disk.  My motherboard doesn't show it in its list of storage devices (which I can bring up by pressing Alt-Esc on boot), but Windows recognized it, and my Linux Mint (based on Ubuntu, so this *does* belong here) disk gave it as an option during install, so I installed Linux onto it, installing GRUB onto the IDE drive.  But now when I boot, I get GRUB Error 21.  What to do?

---

### Post by Pumalite on 2008-03-08
If you can boot a Live CD, from the Terminal, post:
sudo fdisk -lu
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by markekeller on 2008-03-08
Sure, here:

```
mint@mint:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150191684    75095811   83  Linux
/dev/sda2       150191685   156248189     3028252+   5  Extended
/dev/sda5       150191748   156248189     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   160055594    80027766    7  HPFS/NTFS
```

Ah, and I see you're a Mint user too!

---

### Post by Pumalite on 2008-03-08
Mint is great. Your problem is that Windows should be in sda1 and Ubuntu in sdb1. Let's try.
Mount your partition:
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
Now:
cat /media/sda1/boot/grub/menu.lst
Post the output here.

---

### Post by markekeller on 2008-03-08
The output is rather extensive, so I put it in a pastebin instead:

[http://pastebin.ca/934494](http://pastebin.ca/934494)

And by the way, the /dev/hdb1 is what my Windows partition is; it's an IDE drive.  Should it really be listed as sda1?

---

### Post by Pumalite on 2008-03-08
Change this:

#
## ## End Default Options ##
#
 
#
title           Linux Mint, kernel 2.6.22-14-generic
#
root            (hd1,0)
#
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
#
initrd          /boot/initrd.img-2.6.22-14-generic
#
boot
#
 
#
title           Linux Mint, kernel 2.6.22-14-generic (recovery mode)
#
root            (hd1,0)
#
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro single
#
initrd          /boot/initrd.img-2.6.22-14-generic
#
boot
#
 
#
title           Linux Mint, kernel memtest86+
#
root            (hd1,0)
#
kernel          /boot/memtest86+.bin
#
boot
#
 
#
### END DEBIAN AUTOMAGIC KERNELS LIST
#
 
#
# This is a divider, added to separate the menu items below from the Debian
#
# ones.
#
title           Other operating systems:
#
root
#
 
#
 
#
# This entry automatically added by the Debian installer for a non-linux OS
#
# on /dev/hdb1
#
title           Microsoft Windows XP Home Edition
#
root            (hd0,0)
#
savedefault
#
makeactive
#
chainloader     +1
#
 To this:

## ## End Default Options ##

title           Linux Mint, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian ones
title           Other operating systems:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Home Edition
rootnoverify            (hd0,0)
map (hd0,0)  (hd1,0)
map (hd1,0)  (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by markekeller on 2008-03-08
Nope, still the same error. :(

By the way, thanks for that link you posted, lots of really useful stuff there!  From what I read of it, it sounds like that above edit should have solved by problems, but I've still got Error 21.

---

### Post by Pumalite on 2008-03-08
Sorry to hear that. You seem to have the dreaded IDE+SATA mix problem:

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by Pumalite on 2008-03-08
One solution is to install both OS in the same drive and keep the other for data or a separate /home

---

### Post by markekeller on 2008-03-08
Both of those threads had their issues resolved, and their problems seemed different than mine, though . . .

And both on the same disk would work, I bet! But I'd *prefer* to have them separate.  Is there anything else I could do?

---

### Post by markekeller on 2008-03-11
Alright, I've installed Linux on the first hard drive, so it's now sharing it with Windows - and it works!  GRUB recognized the installation on the second drive, now, but I'll edit the GRUB listing to take that out, and I'm going to erase all the files on the second drive and use it for my /home directory and the /usr/local.

And now I've got a different question, related to that - but I'll ask it [in another thread]("http://ubuntuforums.org/showthread.php?p=4497286").

---

