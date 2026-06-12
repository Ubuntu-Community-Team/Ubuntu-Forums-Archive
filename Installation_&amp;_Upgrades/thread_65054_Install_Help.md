---
title: "Install Help"
date: 2005-09-12
forum: Installation &amp; Upgrades
---

### Post by elky10 on 2005-09-12
Hi, I'm new to Linux, and would really like to try Ubuntu, but I'm stuck.  I've gotten through the first part of the install, until it restarts your computer.  I run the Ubuntu selection in Grub ("Ubuntu, kernel 2.6.10-5-386"), but then it displays:

Booting 'Ubuntu, kernel 2.6.10-5-386 '

root  (hd0, 2)
  Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.10-5-386 root =/dev/hde3 ro quiet splash
    [Linux-bzImage, setup=0x1600, size=0x1209f6]
initrd  /boot/initrd.img-2.6.10-5-386
    [Linux-initrd @ 0x3cc7000, 0x426000 bytes]
savedefault
boot
_

That underscore blinks on and off, and nothing happens.  If I press more than fifteen keys, each subsequent keypress (but not keys like shift or control) makes my computer beep.  What should I do?  Should I put the cd back in?  Edit my command options?  Thanks in advance!

---

### Post by rafakl on 2005-09-12
Hi!!!

Please post your computer installed hardware.

---

### Post by elky10 on 2005-09-12
I've got a Pent III, with an Nvidia Riva TNT g-card
Not sure what motherboard I've got, though

Also, I've got two hard drives, I'm dual booting with Windows XP Home, and my main hard drive is partitioned:

1:Windows
2:Shared
3:Linux
4:Swap
(not sure of the exact numbers)

---

### Post by rafakl on 2005-09-12
try editing the command line of gurb and put at the end: acpi=off.

---

### Post by elky10 on 2005-09-12
I put it at the end of kernel, is that where you meant? Cause that didn't work.

---

### Post by rafakl on 2005-09-12
When grub starts, press the e key and then you can edit the line. Put acpi=off at the end.

If it didnt work, please try (put it at the end of the line): noapic nolapic

---

### Post by elky10 on 2005-09-12
I tried both at the line that begins with kernel, but neither worked.   Which line should I put it on?

---

### Post by rafakl on 2005-09-12
There.

Sorry it didnt worked.
 :|

---

### Post by elky10 on 2005-09-13
That's all right.  If anyone else could help, I really want to try Ubuntu...

---

### Post by elky10 on 2005-09-14
Does anyone know what my problem might be?

---

