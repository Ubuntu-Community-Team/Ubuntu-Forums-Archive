---
title: "Problem booting with USB"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by xw92 on 2008-11-04
Hi, I have installed intrepid ibex onto a 1gb USB drive from a live session. however, when i try to boot from the usb, the screen simply shows GRUB _, and freezes. maybe GRUB was not installed onto the usb?

if anyone has a solution, it would be greatly appreciated

thanks in advance

---

### Post by C.S.Cameron on 2008-11-04
Are you using usb-creator or unebootin to make the install?
1G flash drive is large enough, however if using usb-creator you should un-check the part about 128 MB extra space.
I think U-C does not like all flash drives equally.
If you are trying to install to 1G Micro SD USB drive, I have not had much luck booting these myself.

---

### Post by xw92 on 2008-11-04
I was using the usb installer that comes with intrepid.

---

### Post by C.S.Cameron on 2008-11-05
Usb-creator is the usb installer that comes with intrepid. 
I have had grub _ with a blinking _ trying it with 8.10 alpha and beta.
I have not had luck reinstalling grub when this happens.
usb-creator seems to be working ok for me now on partitions under 2G, but not on anything larger,(Kingston drives).
Consider this post a bump, someone else might have an idea.
good luck

---

### Post by caljohnsmith on 2008-11-05
So does the Intrepid USB creator use Grub instead of syslinux like UNetBootin? If so, how about posting:
```

sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
```
Does the Grub find command find the Ubuntu partition on the USB drive? It should be (hdX,Y) where X is 1 or greater. If the find command does locate the USB Ubuntu partition, then finish with:
```
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And please post the output of all the above commands.

---

### Post by C.S.Cameron on 2008-11-05
Thanks for helping caljohnsmith.
Don't think U-C uses grub, think it uses syslinux.
Find /boot/grub/stage1 gives:
Error 15 File not found.
There is no grub folder in the boot folder.
The start menu is found in syslinux/text.cfg.

---

### Post by caljohnsmith on 2008-11-05
> **C.S.Cameron said:**
> Thanks for helping caljohnsmith.
Don't think U-C uses grub, think it uses syslinux.
Find /boot/grub/stage1 gives:
Error 15 File not found.
There is no grub folder in the boot folder.
The start menu is found in syslinux/text.cfg.
Yes, I thought the USB creator would use syslinux, but then why would you be getting a flashing "GRUB" when the USB hangs? How about posting the output of:
```
sudo fdisk -l 2>/dev/null | egrep "Disk /|/dev/" | sed "s#^/dev/#Part /dev/#" | awk '{print $2}' | sed 's/://' | xargs -n1 -iX sudo sh -c "dd if=X count=1 2>/dev/null | grep GRUB > /dev/null && echo Grub found: X || echo no Grub: X"
```
Sorry it's such a long command, but that will tell us which boot sectors on your drives have Grub, and which don't.

---

### Post by C.S.Cameron on 2008-11-05
I'm not the one with the grub problem, but I ran the command with a U-C disk plugged in anyway. (I'm interested).
Got:
no Grub: /dev/sda
no Grub: /dev/sda1
no Grub: /dev/sdb
no Grub: /dev/sdb1
The disk is 2G and has a working U-C install of 8.10
(Both HDD and flash have only one partition).

---

