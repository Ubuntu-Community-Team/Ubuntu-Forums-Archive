---
title: "editing grub gets blank gedit"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by ookooboontoo on 2007-04-24
I repartitioned a disk and removed another. this left me with no functioning Grub. I followed the instructions [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

sudo grub
find /boot/grub/stage1
root (hd5,0)
setup (hd0)
quit

now when I boot I got the list but on clicking the Ubuntu boot, I get an error 17 and it does not load

I have tried 

sudo fdisk -l  gave me 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   6  FAT16
/dev/sda2   *          11        2560    20482875    7  HPFS/NTFS
/dev/sda3            2561        4737    17486752+   5  Extended
/dev/sda4            4738        4864     1020127+  82  Linux swap / Solaris
/dev/sda5            4645        4737      746991   82  Linux swap / Solaris
/dev/sda6   *        2859        4600    13992583+  83  Linux
/dev/sda7            4601        4644      353398+  82  Linux swap / Solaris

Partition table entries are not in disk order

sudo mount /dev/sda2 /mnt gave that it was already mounted

sudo gedit /mnt/boot/grub/menu.list gave me a blank gedit screen


Any Ideas how to edit the grub? I think it is in the mbr

Thanks in advance

---

### Post by taurus on 2007-04-24
/dev/sda2 is your ntfs--Windows!  Looks like your Ubuntu is on /dev/sda6.

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda6 /mnt/ubuntu
**gksudo** gedit /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by indytim on 2007-04-24
Do you really mean that your grub is located on hd5?

> sudo grub
find /boot/grub/stage1
root (hd5,0)
setup (hd0)
quit


I think what you may want is

```

grub> root(hd0)
grub>setup(hd0,5)

```

Just an additional friendly reminder, grub partitions start at "0" and not "1".

IndyTim

---

### Post by ookooboontoo on 2007-04-24
Thank you both for replying, Just to fill in more, I deleted the original hda5 which was a previous ubuntu install hence I have 2 swaps still left. Then, obviously the drive nos moved up.

the ntfs is my original windows. I am hopefully just looking for the grub file to edit it to say where the main drive for linux is and it's swap file

Like I said the grub does now show, but only windows boots from this

I am an intermediate I would think but do be gentle with me :D

---

### Post by ookooboontoo on 2007-04-24
Darn, I did not say, I am trying to edit the Grub using the LiveCD, sorry

---

### Post by ookooboontoo on 2007-04-25
> **taurus said:**
> /dev/sda2 is your ntfs--Windows!  Looks like your Ubuntu is on /dev/sda6.

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda6 /mnt/ubuntu
**gksudo** gedit /mnt/ubuntu/boot/grub/menu.lst
```
Thank you Taurus, Sorry for delay in reply, but only just got round to it. It worked like a dream and you deserve your place in a hall of fame. A point of note, The first two lines went in fine, the last one initially could not work, gave an authentication error and put the piece in some kind of read only. However I pasted exactly the same line in again and it opened gedit successfully and I am now writing this on my reopened old desktop. Its good to be back :)

Indytim, you were right for when I editted the grub itself. I changed all the (hd0,6) to (hd0,5) within grub and that was the fix I needed.

Thank you both.:guitar:

---

