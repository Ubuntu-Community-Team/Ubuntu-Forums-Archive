---
title: "Live Usb how to make"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by ecoooouybe on 2013-06-05
How I can make a live usb with Ubuntu? I have downloading Ubuntu desktop 13.04 x64 with i132, and I have windows 8 pro

---

### Post by slickymaster on 2013-06-05
Hi, ecoooouybe, welcome to the forums.

Here's how to [create a bootable USB stick on Windows]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") and how to [create a bootable USB stick on Ubuntu]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu").

---

### Post by ecoooouybe on 2013-06-05
Yes, I did it. Now, how I can selected windows files from Ubuntu usb live?

---

### Post by slickymaster on 2013-06-05
You probably should be able to see your hard drive in Nautilus. If so, click it and it should mount. Then check your left top where it says ´devices´ for your device and you can browse your files and copy/delete/move them.

If by any chances you're not able to do that, another option is to mount the partition where windows is. Run this on a terminal window:```
sudo fdisk -l
```
The output should be something like```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    8  HPFS/NTFS/exFAT
/dev/sda2          206848   209717247   104755200    8  HPFS/NTFS/exFAT
```
To locate which partition has your files, perform the following command:```
sudo mount -t ntfs-3g /dev/sdaX /~/choose-a-folder-name-you-want
```where X is the number of the partition you want to mount, like /dev/sda1 or /dev/sda2. It should mount the disk with full access, so you can copy and paste files to those folders.
Remember, it will mount your windows 7 partition to a folder, so be carefull not to delete anything important.

---

### Post by ecoooouybe on 2013-06-07
'sudo' is not reconnu en tant que commande interne ou externe, un programme exécutable ou on fichiers de commandes

---

### Post by slickymaster on 2013-06-07
> **ecoooouybe said:**
> 'sudo' is not reconnu en tant que commande interne ou externe, un programme exécutable ou on fichiers de commandes

```
sudo
```is a Unix/Linux command. It looks like you are running this in Windows.

---

### Post by ecoooouybe on 2013-06-07
I digit 'fdisk -l' and 'fdisk' is not identify as command

---

### Post by slickymaster on 2013-06-07
The thing is, where are you running the command?

You have to run it in your Ubuntu partition and it seems you're doing it in your windows partition.

---

