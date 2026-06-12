---
title: "add windows vista manually in GRUB"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by holyct on 2007-11-11
I have Windows XP installed in my hard disk 1st partition.

I use Norton Ghost copy Vista into my 2nd partition, which is a logic drive. Since it is a disk to disk copy, Vista did not modify my MBR.

Then I install Ubuntu in 3rd partition, but GRUB only recognize Windows XP, now I want to manually add Vista into GRUB, is it possible?

---

### Post by eggdeng on 2007-11-11
This is not going to work. To begin with, Microsoft OSs need to be installed on primary partitions. Neither can you just ghost Vista (or XP for that matter) from box to box the way you could with Win98 without running into product activation problems. 
You could try pointing grub at the Vista install by adding the following stanza to your /boot/grub/menu.lst to see what happens.
```
title		Windows Vista
root		(hd0,1)
chainloader	 +1 
```

---

### Post by meierfra on 2007-11-11
The first logical partiton is (hd0,4), the second (hd0,5) and so on.  So I would guess that Vista is on (hd0,4).

So I would try 

title		Windows Vista
rootnoverify		(hd0,4)
chainloader	 +1


 To find out for sure look at output of 

sudo fdisk -l

If vista is  sda5 (or hda5) then  the grub name for vista will be (hd0,4). If it is sda6, it will be  (hd0,5) (Always one less, since Grub starts counting at 0).

---

