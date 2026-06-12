---
title: "Question about the bootloader installation part"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by andrewwg94 on 2008-11-07
in step 7/7, there's an 'advanced' button, when i click on that, it lets me choose where to install GRUB. What happends if i tell it to install it on my Windows Partition?

---

### Post by cdtech on 2008-11-07
This will install the GRUB bootloader to the "master boot record" of your primary drive (which is what you probably want). Unless you plan on booting from another device. With this you will be prompted with the GRUB boot menu on boot with a selection of operating systems installed on your computer.

Hope this helps ya........

---

### Post by meierfra. on 2008-11-07
[QUOTE=andrewwg94]That happends if i tell it to install it on my Windows Partition?
[/QUOTE]

[QUOTE=cdtech]This will install the GRUB bootloader to the "master boot record" of your primary drive (which is what you probably want).[/QUOTE]


Wrong. That will overwrite the boot sector of your Windows partition and you won't be able to boot into Windows anymore.

---

### Post by cdtech on 2008-11-07
> **meierfra. said:**
> Wrong. That will overwrite the boot sector of your Windows partition and you won't be able to boot into Windows anymore.

Do what?

If he has one drive (as in dual boot) then the MBR is his windows partition. Without the GRUB bootloader on the MBR he wont be able to boot into Ubuntu.

If Windows is the primary drive and you have Ubuntu installed on a second drive then the choice is yours. You would have to select the drive to boot from within the BIOS.

---

### Post by meierfra. on 2008-11-07
> Do what?
?????

Installing Grub to the Windows partition, overwrites the Windows boot sector.  That is definitely not what the OP wants.

> 
The MBR is his windows partition

No!

The MBR comes before any partition. To install Grub to the MBR of the boot drive one needs to choose (hd0) after clicking on  the advanced button.(or (hd1) for the MBR of the second hard drive)

---

### Post by cdtech on 2008-11-07
My bad, I stand corrected. I misread thinking he wanted to install to the windows drive and not the partition. You are correct about The MBR is not located in a partition, it is located at a Main Boot Record area in front of the partition.

Sorry.........

---

### Post by meierfra. on 2008-11-07
andrewwg94:

Just in  case you already did install grub to the Windows partition:

You can restore the Windows boot sector via

```
fixboot
```

from repair console of the XP CD or via

```
bootrec /fixboot
```

for the Vista CD.

If you do not have a  Windows CD, just let me know and I can show you how to  uses "testdisk" from Ubuntu to fix the boot sector.

---

### Post by andrewwg94 on 2008-11-07
> **meierfra. said:**
> andrewwg94:

Just in  case you already did install grub to the Windows partition:

You can restore the Windows boot sector via

```
fixboot
```

from repair console of the XP CD or via

```
bootrec /fixboot
```

for the Vista CD.

If you do not have a  Windows CD, just let me know and I can show you how to  uses "testdisk" from Ubuntu to fix the boot sector.

thanks for the info guys, i was wondering what that fixboot command did. So every partition has a boot sector before it? or just the windows partition?

---

### Post by meierfra. on 2008-11-08
> So every partition has a boot sector before it? or just the windows partition?

Every partition has  boot sector,  but  it  is not before the partition, it's the very first sector of the partition. 

Although the boot sector of the Ubuntu partition  isn't used for much, unless you install grub to it.

---

