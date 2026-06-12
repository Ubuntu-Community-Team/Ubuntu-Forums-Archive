---
title: "ubuntu doen't display boot menù"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Garabombo on 2008-10-31
I'm a new user and installed ubuntu 8.04 on the second hard drive of my PC, while on the first I had previously installed XP.
At the boot time, the system doesn't display the menù from which to select the booting option. 
I followed the procedure described in the reply posted by herman on November 11th, 2007,regarding hot to install boot loader from ubuntu but it does not work.
I hope somebody can help me

---

### Post by caljohnsmith on 2008-10-31
First, please boot your Live CD, open a terminal (applications > accessories > terminal), and post:
```
sudo fdisk -lu
```
Also, can you go into your BIOS and change the boot order? It would be most ideal if you can do that so you can boot directly from the Ubuntu drive and not the Windows drive.

---

### Post by Garabombo on 2008-10-31
here itis the output of fdisk
Disco /dev/sda: 61.4 GB, 61492838400 byte
255 heads, 63 sectors/track, 7476 cylinders, totale 120103200 settori
Units = settori of 1 * 512 = 512 bytes
Disk identifier: 0x03af03af

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS

Disco /dev/sdb: 122.9 GB, 122942324736 byte
255 heads, 63 sectors/track, 14946 cylinders, totale 240121728 settori
Units = settori of 1 * 512 = 512 bytes
Disk identifier: 0xaeabaeab

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   120101939    60050938+   7  HPFS/NTFS
/dev/sdb2       120101940   240107489    60002775    5  Esteso
/dev/sdb5       120102003   237087269    58492633+  83  Linux
/dev/sdb6       237087333   240107489     1510078+  82  Linux swap / Solaris

I also tried to set the ubuntu hd as  boot hd but inthiscase the system dos not boot at all.

---

### Post by caljohnsmith on 2008-10-31
Can you boot your sda Windows drive at all? From you Live CD, do the following to install Grub to the MBR (Master Boot Record) of you sdb drive:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
Reboot, set your BIOS to boot the sdb drive, and let me know if you get a Grub menu. If you do get the Grub menu, most likely you won't be able to boot Ubuntu or Windows; but see if you can get as far as a Grub menu, and we can work from there.

---

### Post by Garabombo on 2008-10-31
nothing is changed, again the system does not boot from the second drive. So I restored the firstdrive as boot drive and again the menù does not appear and ubunto starts

---

### Post by caljohnsmith on 2008-10-31
OK, how about posting:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
Next post:
```
sudo mount /dev/sdb5 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by Garabombo on 2008-10-31
Done. And now?

---

### Post by 4uvak91 on 2008-10-31
> **caljohnsmith said:**
> Can you boot your sda Windows drive at all? From you Live CD, do the following to install Grub to the MBR (Master Boot Record) of you sdb drive:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
Reboot, set your BIOS to boot the sdb drive, and let me know if you get a Grub menu. If you do get the Grub menu, most likely you won't be able to boot Ubuntu or Windows; but see if you can get as far as a Grub menu, and we can work from there.


how do youk now hich HDD it's?? i have same problem....

---

