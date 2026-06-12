---
title: "Entirely lost grub access on reboot-help!"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Daveth on 2007-03-03
oops, playing around with E17 after logging out of gnome and accidentally mapped my left mouse click to window shifting, so could not get out of anything. In desparation I hit the PC reset button, but on rebooting there was no grub bootloader, so no ubuntu dapper or XP. 
PC went to my second drive and found that xp copy and xandros, but that did not go anywhere.

I'm doing this from the live ubuntu cd.

So, any ideas how I recover my bootloader? Not even sure how to get to a command line- can I rescue it from this live cd, and how????

In slight panic
Daveth

---

### Post by taurus on 2007-03-03
What partition is your Ubuntu's /?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Daveth on 2007-03-03
/dev/sda2


/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       30023   138761437+  83  Linux
/dev/sda3           30024       30401     3036285    5  Extended
/dev/sda5           30024       30401     3036253+  82  Linux swap / Solaris

---

### Post by Daveth on 2007-03-03
if it helps, the results of looking for boot/grub/stage1 show that it is on Hd1,1, - so not the Sata disk but on the old ide?

/dev/hdb1   *           1        5467    43913646    7  HPFS/NTFS
/dev/hdb2            5468        9964    36122152+   5  Extended
/dev/hdb5            5468        5532      522081   82  Linux swap / Solaris
/dev/hdb6            5533        9964    35600008+  83  Linux

where the old copy of Xandros and the original XP reside. Ubuntu, as I said, lives with a new XP install on the sata disk (sda)

---

### Post by Daveth on 2007-03-04
I tried this thread

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

and Catlett's fix, but get an error message about expecting a number when I try the setup to install grub to the mbr option. 

I'm assuming it is setup (sd0,0) but it rejects this and (sd0) as options. I don't actually know if this is where the mbr is, or what re-installing grub will do to XP. I do not want to re-load grub in the wrong place

Can anyone suggest a way through please ???

---

### Post by bulldog on 2007-03-04
Grub make no difference between sata and ide disk.
They are called (hd0) and (hd1) and so on.
To understand how ubuntu is naming your disks```
cat /boot/grub/device.map
```

You have to install Grub on (hd0) or (hd1),not (sd0).

---

### Post by Daveth on 2007-03-04
yes, I just found that out on another forum, but thank you anyway. However, I have now hit an error 17 message.
I followed Catlett's rules, so, as root, 
grub
root (hd,1,1)
setup (hd0)

then rebooted as he states.
But got error 17, cannot mount selected partitions, unknown filesystem, root (hd0,1)

XP was v upset when I tried it from grub. Grub loaded with all the kernels, but did not lead anywhere.
So, still stuck

---

### Post by Daveth on 2007-03-05
Now got it re-loaded and this is the menu.lst


title           Ubuntu, kernel 2.6.15-28-k7
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-k7 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-k7
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-k7 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-k7 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-28-k7
boot

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify            (hd0,0)
savedefault
makeactive
chainloader     +1

I added rootnoverify to the XP section, but this made no difference. It continues to throw up Error 17, unknown filesystem, cannot mount selected partition.  It has root hd0,1 and root = /dev/sda2. Obviously something is not pointing in the right place, but I'm now so confused I cannot see a way through.

Can anyone suggest something other than re-installing the whole damn thing???

---

