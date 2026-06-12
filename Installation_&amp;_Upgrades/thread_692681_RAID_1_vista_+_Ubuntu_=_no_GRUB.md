---
title: "RAID 1 vista + Ubuntu = no GRUB?"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by Elusid on 2008-02-10
I have 3 HDDs and two of them are in RAID 1 with Vista which is my primary boot device which (for some reason) can't be changed. Then I also have Ubuntu on the 3rd HDD which I put on after vista. For some reason it didn't put GRUB on the MBR when I installed Ubuntu so how would I go about installing GRUB so that it will work with my RAID 1 vista partition and ubuntu hdd.

---

### Post by apedeaux on 2008-06-02
This is exactly the problem I have... 2 SATAs RAIDed running XP, got a brand new SATA to install Ubuntu completely seperate from the XP/RAID, but I can't boot from the Linux drive because apparently GRUB is missing/on the wrong drive.

---

### Post by meierfra. on 2008-06-03
This will install grub to the Linux drive. Boot from a LiveCD.

```
sudo grub
```
and at the grub prompt:


```
find /boot/grub/menu.lst
```
(l is a lowercase L)

The output will be of the form "(hd2,0)", but the numbers might be different.

Then (still at the grub prompt)

```

root (hd2,0)  #  use the output from the previous command
setup (hd2)     #  use the first number of the output
quit
```

Reboot and you should get to the Grub menu (Press "esc" if necessary)

Select ubuntu, but do not press enter, press "e" instead. Press "e" again to edit the first line.

Change "root (hd2,0)" to "root (hd0,0)" (so change the first number to "0", but do not change the second number)

Press "enter" and then "b" to boot.

If this work, you need to edit "menu.lst"  after you booted into ubuntu

```
gksudo gedit /boot/grub/menu.lst
```

change  "#groot (hd2,0)" to "#groot (hd0,0)". (Change it the same way you changed "root ...")

Save the file. In the terminal:

```
sudo update-grub
```

---

