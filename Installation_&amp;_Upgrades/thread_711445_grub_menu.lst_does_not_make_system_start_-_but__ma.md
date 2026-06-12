---
title: "grub menu.lst does not make system start - but  manual entries make system run !"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by kerkael on 2008-02-29
Hi there,

I installed my 6.10 Dapper Ubuntu on my HDD while connected as USB from another laptop.
As unique hdd at the installation time, it was seen as **(hd0,0)** but **/dev/sda1 **

When I put that hdd back into the dedicated laptop, it's still **(hd0,0)** but now its  **/dev/hda1 **

The problem is the grub menu.lst points on /dev/sda1 for the kernel line.
I tried to add another choice in my menu for the kernel to point on /dev/hda1 but it does not work.

Original menu entries :
```
 Booting 'Ubuntu on sda1'
root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel   /boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet
initrd    /boot/initrd.img-2.6.15-26-386
savedefault
boot
```
When booting from that entry, I get that :
[FONT="Courier New"]Uncompressing Linux... Ok, booting the kernel.
[17179569.184000] ACPI: Unable to locate RSDP
[  195.887241] hub 1-0:1.0: over-current change on port 2
ALERT! /dev/sda1 does not exist. Dropping to a shell![/FONT]

I tried just to modify the** root=/dev/sda**1 into **/dev/hda1**. Then I get that :
[FONT="Courier New"]Error 15 : File Not Found[/FONT]

But, if I press 'c' while on grub choices and try to boot manualy, **It works !**
```
grub> kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1
grub> initrd    /boot/initrd.img-2.6.15-26-386
grub> boot
```
There I get my system to boot.

Could someone tell me why manual entry of the exact same line as proposed in my menu.lst works where the menu.lst gets an error 15 ? I don't really want to boot manually.

Thank you all

---

### Post by logos34 on 2008-02-29
It's probably either your uncorrected fstab or device.map file.  Change them to read hda1:

gksudo gedit /etc/fstab

gksudo gedit /boot/grub/device.map

---

