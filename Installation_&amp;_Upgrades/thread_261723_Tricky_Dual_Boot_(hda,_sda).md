---
title: "Tricky Dual Boot (hda, sda)"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by krojc on 2006-09-20
Hello, guys.

It goes as follows. I had a sata disk that was occupied by XP and I added a ide drive containing ubuntu. The idea was to add this ide to windows boot.ini using linux.bin produced by dd if=linux.bin..., since this drive goes in and out of the box. I used boot floppy to get into the ubuntu and successfully called the configfile using:

configfile (hd1,0)/boot/grub/menu.lst

When the menu loaded it produced an error since root is at (hd1,0), while menu.lst searched for (hd0,0). Edited the entry and I was good to go.
When in terminal I checked the drive and it said it is located at /dev/hda1, while XP is on /dev/sda1. I reinstalled grub to this /dev/hda1 location and made a dd if=linux.bin of=/dev/hda1... which was copied to c:\

When booting the XP menu goes up, but after calling Linux drive all I get is GRUB and blinking _. XP works normaly.

Order in bios is 1st sata, 2nd ide. If I change the order the grub pops up perfectly., but then the XP fails

The Q is how to make a linux.bin to load grub from XP when obviously drives change order.

devices.map
/dev/sda (hd0,0)
/dev/hda (hd1,0)

menu.lst
all entries call (hd1,0)

Thanks in advance. I know someone already got this. I've done this on ide's so many times, that this one really gets my temperature up.

---

### Post by krojc on 2006-09-21
Anyone, please :(

---

