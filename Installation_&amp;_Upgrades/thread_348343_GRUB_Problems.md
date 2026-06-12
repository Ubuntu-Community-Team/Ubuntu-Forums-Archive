---
title: "GRUB Problems"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by Kuma_Pageworks on 2007-01-28
Hi there - I've tried every method described in the HOWTO threads here, and I still can't get Ubuntu to dual-boot with my XP installation.  Let me describe my setup:

160 GB SATA drive:
/dev/sda1: 140 GB partition with Windows on it.
/dev/sda2: 10 GB partition that had my recovery DVDs on it - now it's just extra space.

100 GB IDE drive:
/dev/hdd1: 64 GB partition - NTFS storage.
/dev/hdd2: 30 GB partition - Ubuntu installation.
/dev/hdd3: 1 GB partition - Ubuntu swap.

I've tried the Super GRUB Disk and the other methods, but I can't get GRUB to come up when I boot (actually, I got it to come up exactly once for some unknown reason).

I've been using the Live CD to get into my Ubuntu installation and modify GRUB, and it says that it's ended successfully, but every reboot I go directly into XP.

Do I need to move Ubuntu to the primary partition on the 2nd drive in order for it to work?  It seems like GRUB is writing to the MBR of the 2nd disk instead of the 1st disk - it identifies the IDE drive (the slave drive) as hd0 ... could that be my problem?

Thanks much.

---

### Post by Ramses de Norre on 2007-01-28
This is the code you need to run:
```
sudo grub
root (hd?,?)
setup (hd?)
quit
```
To find out what to fill in for the "?" you mount your ubuntu partition and open /boot/grub/device.map which contains a list with the grub names for your devices, the one your looking for is starting with "sd". So if there's a line "(hd1)    /dev/sda" the commands become:```
sudo grub
root (hd1,1)
setup (hd1)
quit
```
(hd1,1):second partition of second drive (grub counts from zero, second drive because it's set so in device.map(assumption)).
(hd1):the second's drive MBR.

---

### Post by pyromithrandir on 2007-01-28
It's actually even easier than that. If you are already logged into your Ubuntu system, just type ```
sudo grub-install /dev/sda
```

---

### Post by Kuma_Pageworks on 2007-01-28
> **pyromithrandir said:**
> It's actually even easier than that. If you are already logged into your Ubuntu system, just type ```
sudo grub-install /dev/sda
```

Will that work from the Live CD?  Or do I need to mount the installation first?

---

### Post by Kuma_Pageworks on 2007-01-28
> **Ramses de Norre said:**
> This is the code you need to run:
```
sudo grub
root (hd?,?)
setup (hd?)
quit
```
To find out what to fill in for the "?" you mount your ubuntu partition and open /boot/grub/device.map which contains a list with the grub names for your devices, the one your looking for is starting with "sd". So if there's a line "(hd1)    /dev/sda" the commands become:```
sudo grub
root (hd1,1)
setup (hd1)
quit
```
(hd1,1):second partition of second drive (grub counts from zero, second drive because it's set so in device.map(assumption)).
(hd1):the second's drive MBR.

I'll give that a shot - as I read the fdisk -l, there's an asterisk by the first partition, which I assume means that it's the partition that the MBR points to.  I'll let you know.

---

### Post by pyromithrandir on 2007-01-28
You can use the grub-install command from the LiveCD, but you'll have to mount your linux root partition and give it to the command withthe 
--root-directory=DIR option

For example:
mkdir UbuntuInstall
sudo mount /dev/hdd2 UbuntuInstall
sudo grub-install --root-directory=./UbuntuInstall /dev/sda

---

